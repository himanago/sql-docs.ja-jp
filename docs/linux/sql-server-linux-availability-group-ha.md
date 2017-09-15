---
title: "SQL Server Always On 可用性グループ配置のパターン |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/16/2017
ms.prod: sql-linux
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 353e7cf5cef8430303e3ee6fbefc92db08f5f733
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="high-availability-and-data-protection-for-availability-group-configurations"></a>可用性グループの構成の高可用性とデータの保護

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

この記事では、Linux サーバー上の SQL Server Always On 可用性グループのサポートされる展開構成を表示します。 可用性グループには、高可用性とデータ保護がサポートしています。 障害の自動検出、自動フェールオーバー、およびフェールオーバー後に透過的な再接続は、高可用性を実現します。 同期されたレプリカは、データ保護を提供します。 

>[!NOTE]
>高可用性とデータ保護、だけでなく、可用性グループことができますも災害復旧を実現、クロス プラットフォームの移行、およびスケール アウトを読み取る。主に、高可用性とデータ保護の実装について説明します。 

Windows Server フェールオーバー クラスタ リングで、一般的な構成の高可用性を使用する 2 つのレプリカを同期し、[ファイル共有監視](http://technet.microsoft.com/library/cc731739.aspx)です。 ファイル共有監視は、たとえば、可用性グループの構成で、同期の状態と、レプリカのロールを検証します。 この構成により、セカンダリ レプリカのフェールオーバー ターゲットがある最新のデータと可用性グループ構成の変更として選択します。 

Linux 用の現在の高可用性ソリューションを Windows Server フェールオーバー クラスターでファイル共有監視のような外部にミラーリング監視サーバーに対応していません。 Windows Server フェールオーバー クラスターがない場合は、可用性グループの構成が参加している SQL Server インスタンスの master データベースに格納されます。 したがって、可用性グループでは、高可用性とデータ保護のためには、少なくとも 3 つの同期レプリカが必要です。 Linux サーバーの可用性グループを作成した後は、クラスター リソースを作成します。 クラスター リソースの設定は、高可用性の構成を決定します。

スケール アウトを読み取ったりする高可用性、データ保護に関する特定のビジネス要件に対応する可用性グループの設計を選択します。

>[!IMPORTANT]
>次の構成は、可用性グループのデザイン パターンと、各パターンの機能について説明します。 これらの設計パターンを持つ可用性グループに適用`CLUSTER_TYPE = EXTERNAL`高可用性ソリューションにします。 

デザイン パターンは、次の 2 つの可用性グループの構成です。 構成は次のとおりです。

- **次の 3 つの同期レプリカ**

- **2 つの同期レプリカ**

## <a name="how-the-configuration-affects-default-resource-settings"></a>既定のリソース設定の構成の影響

クラスター リソース設定`required_synchronized_secondaries_to_commit`各トランザクションでは、プライマリ レプリカ上でトランザクションをコミットする前にセカンダリ レプリカのログの最小数を書き込むことが保証されます。 この設定は、高可用性と構成に応じて、データ保護の両方に影響します。 エージェント インストールすると、SQL Server リソースの`mssql-server-ha`-可用性グループのクラスター リソースを作成、クラスター マネージャーの可用性の検出し構成と設定をグループ化`required_synchronized_secondaries_to_commit`それに応じて。 

リソースのエージェント パラメーターの構成でサポートされている場合`required_synchronized_secondaries_to_commit`が高可用性とデータ保護を提供する値に設定します。 詳細については、次を参照してください。[ペースの SQL Server の理解リソース エージェント](#pacemakerNotify)です。

次のセクションでは、クラスター リソースの既定の動作を説明します。 

<a name="threeSynch"></a>

## <a name="three-synchronous-replicas"></a>次の 3 つの同期レプリカ

この構成は、次の 3 つの同期レプリカで構成されます。 既定では、高可用性とデータ保護を提供します。 読み取りのスケール アウトが提供することもできます。

![3 つのレプリカ][3]

次の表には、3 つの同期レプリカがある可用性グループの設定に基づく高の可用性とデータ保護の動作がについて説明します。 

|`required_synchronized_secondaries_to_commit`|0 |1 \*|2
| --- |:---:|:---:|:---:
|プライマリ レプリカの停止後に自動フェールオーバー| |✔| 
|プライマリ レプリカの 1 つのセカンダリ レプリカの停止後に使用できます。|✔|✔| 
|2 つのセカンダリ レプリカの停止後に利用可能なプライマリ レプリカ|✔| |
|プライマリ レプリカの停止 - データの損失後に手動フェールオーバー|✔| | 

\*既定の設定、クラスター内のリソースとして可用性グループが追加されるとき。

<a name="twoSynch"></a>

## <a name="two-synchronous-replicas"></a>2 つの同期レプリカ

この構成は、データの保護を実現します。 その他の可用性グループ構成のように読み取りのスケール アウトを有効にできます。2 つの同期レプリカの構成は、自動の高可用性を提供しません。 

![2 つの同期レプリカ][1]

この構成では、2 つのサーバーが必要です。 これらのサーバーでは、プライマリ レプリカとセカンダリ レプリカのロールを入力します。 

データの最適な 2 つの同期レプリカ構成の保護とデータベースの読み取りワークロードを分散します。 既定では、データの保護に関するリソースが構成されます。 この構成は、SQL Server のいずれかのインスタンスが失敗した場合、データベースが完全に使用可能かデータ損失のリスクがあるために、高可用性を提供しません。 

次の表では、2 つの同期レプリカがある可用性グループの有効な値に従ってデータ保護の動作について説明します。 

|`required_synchronized_secondaries_to_commit`|0 \*|1 
| --- |:---|:---
|プライマリ レプリカの停止後に自動フェールオーバー| |✔ \*\* | 
|プライマリ レプリカのセカンダリ レプリカの停止後に使用できます。|✔| |

\*既定の設定、クラスター内のリソースとして可用性グループが追加されるとき。

\*\*この構成は、自動の可用性グループをプライマリ レプリカの停止が発生した後は、経由で失敗します。 アプリケーションは、プライマリ レプリカは、行に戻るようになりました、セカンダリ レプリカとしてまで、可用性グループに接続できません。 

2 つの同期レプリカの構成は、2 台のサーバーで SQL Server の 2 つのインスタンスのみが必要なために、最も経済的なことがあります。

<a name="pacemakerNotify"></a>

## <a name="understand-sql-server-resource-agent-for-pacemaker"></a>ペースに対する SQL Server エージェントのリソースを理解します。

SQL Server 2017 CTP 1.4 追加`sequence_number`に`sys.availability_groups`レプリカがプライマリ レプリカとが最新であるかのセカンダリを識別するペースを許可します。 `sequence_number`最新であるか、ローカルの可用性グループのレプリカを表す単調に増加する bigint 型の値です。 ペースの更新プログラム、`sequence_number`可用性グループの構成変更のたびにします。 構成の変更には、フェールオーバー、レプリカの追加または削除などがあります。 数が、プライマリ上で更新し、セカンダリ レプリカにレプリケートします。 このため、最新の状態の構成を持つセカンダリ レプリカは、プライマリと同じシーケンス番号です。 

最初は送信をプライマリ レプリカを昇格するペースが決定したら、*事前昇格*すべてのレプリカに通知します。 レプリカは、シーケンス番号を返します。 次に、ペースが実際には、レプリカはプライマリに昇格しようとするとき、レプリカのみ昇格自体のシーケンス番号が、すべてのシーケンス番号の最も高い場合。 独自のシーケンス番号が一番大きいシーケンス番号が一致しない場合、レプリカは、昇格操作を拒否します。 この方法により、最大のシーケンス番号を持つレプリカだけがプライマリに昇格できるようになるため、データの損失が回避されます。 

このプロセスでは、以前のプライマリと同じシーケンス番号を持つプロモーションの利用可能な少なくとも 1 つのレプリカが必要です。 ペース リソース エージェント セットを使用すると、`required_synchronized_secondaries_to_commit`になるようには、少なくとも 1 つの同期セカンダリ レプリカは最新であり、既定では、自動フェールオーバーのターゲットに使用できます。 各監視のアクションの値に`required_synchronized_secondaries_to_commit`計算 (および必要に応じて更新) します。 `required_synchronized_secondaries_to_commit`値は 2 で 'の同期レプリカの数' 割った値します。 フェールオーバー時に、リソースのエージェントが必要です (`total number of replicas`  -  `required_synchronized_secondaries_to_commit`レプリカ) に応答する、事前の通知を昇格します。 最高の値を持つレプリカ`sequence_number`がプライマリに昇格します。 

たとえば、次の 3 つの同期レプリカの 1 つのプライマリ レプリカと 2 つの同期セカンダリ レプリカを可用性グループです。

- `required_synchronized_secondaries_to_commit`1 になります。(3 -> 1 の 2/)。

- 事前昇格アクションに応答するレプリカの必要な数は 2 です。(3-1 = 2)。 

このシナリオでは、2 つのレプリカは、フェールオーバーをトリガーする応答する必要です。 最新の状態にして、応答、プライマリ レプリカの停止後に自動フェールオーバーを正常に実行、両方のセカンダリ レプリカが必要な事前の通知を昇格します。 Online と同期する場合は、同じシーケンス番号があります。 可用性グループを使用して、それらの 1 つ昇格させます。 応答するセカンダリ レプリカの 1 つだけの場合、事前昇格アクション、リソース エージェントは、応答したセカンダリが最高の sequence_number され、フェールオーバーがトリガーされないことを保証ことはできません。

>[!IMPORTANT]
>`required_synchronized_secondaries_to_commit` が 0 の場合、データ損失のリスクがあります。 プライマリ レプリカの停止中に、リソースのエージェントに自動的にフェールオーバーは発生しません、します。 プライマリへの回復を待つか、手動フェールオーバーを使用することができます`FORCE_FAILOVER_ALLOW_DATA_LOSS`です。

既定の動作をオーバーライドして、可用性グループ リソースも設定することもできます`required_synchronized_secondaries_to_commit`自動的にします。

次のスクリプト セット`required_synchronized_secondaries_to_commit`という名前の可用性グループに対して、0 に`<**ag1**>`です。 置換を実行する前に`<**ag1**>`可用性グループの名前に置き換えます。

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=0
```

可用性グループ構成の実行に基づいて、既定値に戻すには。

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=
```

>[!NOTE]
>上記のコマンドを実行すると、プライマリが一時的に降格セカンダリ、し、もう一度昇格されます。 リソースの更新では、すべてのレプリカを停止し、再起動が発生します。 新しい値`required_synchronized_secondaries_to_commit`、瞬時にないレプリカが再起動したら、のみ設定します。

<!--Image references-->
[1]: ./media/sql-server-linux-availability-group-ha/1-read-scale-out.png
[3]: ./media/sql-server-linux-availability-group-ha/3-three-replica.png