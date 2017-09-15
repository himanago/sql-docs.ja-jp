---
title: "パブリケーション情報、トレーサー トークン (SQL Server 2005 以降) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.publicationinfo.tracertokens.f1
ms.assetid: a115ba95-17ae-45df-91bd-5a1a35f3745f
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9302b3bcfea0b63fe4eefdc2c7c03716eaaefa09
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="publication-information-tracer-tokens-sql-server-2005-and-later"></a>パブリケーション情報、トレーサー トークン (SQL Server 2005 以降)
  **[トレーサー トークン]** タブを使用すると、接続の検証と、トランザクション レプリケーションを使用するシステムの待機時間を測定できます。 トークン (小さなデータ) は、通常のレプリケートされたトランザクションのようにマークが付けられてパブリケーション データベースのトランザクション ログに書き込まれ、システムを介して送信されることで、次の計算が可能になります。  
  
-   パブリッシャーでコミットされるトランザクションと、ディストリビューターでディストリビューション データベース内に挿入される対応するコマンドの間での経過時間。  
  
-   ディストリビューション データベース内に挿入されるコマンドと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間。  
  
 これらの計算結果から、以下のようなさまざまな内容を特定できます。  
  
-   変更内容をパブリッシャーから受信するのに最も時間がかかるのはどのサブスクライバーか。  
  
-   トレース トークンを受信することになっているサブスクライバーのうち、受信していないサブスクライバーがあるか。あるとすればどのサブスクライバーか。  
  
## <a name="options"></a>オプション  
 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。  
  
-   **[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。  
  
-   **[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。  
  
-   **[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 **[トレーサーの挿入]**  
 パブリッシャーでトランザクション ログ内のトレーサー トークンを挿入します。  
  
 **[挿入された時間]**  
 トレーサー トークンが挿入された時間を選択し、その時間の待機時間情報を表示します。 既定では、最新の時間の情報が表示されます。  
  
> [!NOTE]  
>  トレーサー トークン情報は、ディストリビューション データベースの履歴保持期間の制約を受けるその他の履歴データと同じ期間保持されます。 ディストリビューション データベースのプロパティの変更方法の詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。  
  
 **サブスクリプション**  
 パブリケーションに対する各サブスクリプションの名前です。  
  
 **[パブリッシャーからディストリビューターまで]**  
 パブリッシャーでコミットされるトランザクションと、ディストリビューターでディストリビューション データベース内に挿入される対応するコマンドの間での経過時間です。 **[保留中]** の値は、トークンがまだディストリビューターに到達していないことを示します。 保留中の状態が続く場合は、ログ リーダー エージェントが実行されていることを確認します。  
  
 **[ディストリビューターからサブスクライバーまで]**  
 ディストリビューション データベース内に挿入されるコマンドと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間です。 **[保留中]** の値は、トークンがまだサブスクライバーに到達していないことを示します。 保留中の状態が続く場合は、ディストリビューション エージェントが実行されていることを確認します。  
  
 **[合計待機時間]**  
 パブリッシャーでコミットされるトランザクションと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間です。 これは、この時間にレプリケーション システムの端末間でサブスクライバーを待機する時間を表しています。 **[保留中]** の値は、トークンがまだサブスクライバーに到達していないことを示します。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [レプリケーション モニターを使用したパフォーマンスの監視](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  