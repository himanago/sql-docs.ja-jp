---
title: "復元シーケンスの計画と実行 (完全復旧モデル) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restore sequences [SQL Server], planning for
- full recovery model [SQL Server], planning restore sequences
ms.assetid: 9cbefaf8-d2b6-41c9-83fc-b3807a841fe2
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 92fca3a74586d7c7adbe135422283342db36a204
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="plan-and-perform-restore-sequences-full-recovery-model"></a>復元シーケンスの計画と実行 (完全復旧モデル)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、主に完全復旧モデルが使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの復元シーケンスを計画し、実行する方法について説明します。 *復元シーケンス* は、1 つ以上の連続した [RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) ステートメントです。 通常、復元シーケンスでは、復元対象のデータベース、ファイル、ページのコンテンツの初期化 (データ コピー フェーズ)、ログに記録されたトランザクションのロールフォワード (再実行フェーズ)、コミットされていないトランザクションのロールバック (元に戻すフェーズ) が実行されます。  
  
 単純な復元シーケンスの場合、必要なのはデータベースの完全バックアップ、差分バックアップ、およびそれ以降のログ バックアップのみです。 このような場合は、適切な復元シーケンスの構築は簡単です。 たとえば、障害が発生した時点までデータベース全体を復元するには、まずアクティブなトランザクション ログ (ログの *末尾* ) をバックアップします。 次に、データベースの最新の完全バックアップ、最新の差分バックアップ (存在する場合) の順に復元してから、それ以降のすべてのログ バックアップを作成順に復元します。  
  
 適切な復元シーケンスの構築がもっと複雑になる場合もあります。 たとえば、複数のファイル バックアップが必要になったり、特定の時点へのデータの復元が必要になる場合があります。 非常に複雑な復元シーケンスでは、1 つ以上の復旧分岐にまたがる、分岐した復旧パスをたどることが必要になる場合もあります。  
  
> [!NOTE]  
>  *復旧パス* は、データベースをある特定の時点 (復旧ポイント) の状態にするための、連続したデータおよびログ バックアップです。 復旧パスは、データベースの一貫性を維持しつつ、その内容がどのような操作によって、時間の経過と共にどのように変化してきたかを具体的に表します。 開始ポイント (LSN、GUID) から終了ポイント (LSN、GUID) までの一連の LSN が 1 つの復旧パスとなります。 復旧パスの LSN は、開始ポイントから終了ポイントまですべてが 1 つの復旧ブランチに属する場合もあれば、複数の復旧ブランチに属する場合もあります。  
  
## <a name="to-plan-a-restore-sequence"></a>復元シーケンスを計画するには  
 復元シーケンスを開始する前に、次の手順を実行します。  
  
1.  データベースのログ末尾のバックアップを (作成できる場合は) 作成します。 詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)」を参照してください。  
  
2.  目的の復旧ポイントを決定します。  
  
     目的の復旧ポイントとして、トランザクション ログ バックアップ内の任意の時点またはマークを選択することができます。 詳細については、「[SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)」または「[マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)」を参照してください。  
  
3.  実行する復元の種類を決定します。 詳細については、「 [復元と復旧の概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)」を参照してください。  
  
4.  必要なバックアップを特定し、必要なメディア セットとバックアップ デバイスが使用可能であることを確認します。 詳細については、「[バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)」と「[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。  
  
## <a name="to-perform-a-restore-sequence"></a>復元シーケンスを実行するには  
 復元シーケンスを実行するには、次の手順を実行します。  
  
1.  シーケンスを開始するために、データベース バックアップ、部分バックアップ、1 つ以上のファイル バックアップなど、1 つ以上のデータ バックアップを復元します。  
  
2.  必要に応じて、これらの完全バックアップを基にした最新の差分バックアップを復元します。  
  
     復元する各完全バックアップがいずれかの差分バックアップのベースであるかどうかを確認します。 その場合は、最新の差分バックアップを (復元できる場合は) 復元します。 詳細については、「[差分バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)」を参照してください。  
  
3.  ログ バックアップを順番に復元することによって、データベースをロールフォワードします。最後に復旧ポイントを含むログ バックアップを復元します。 すべてのログ バックアップを適用する必要があるかどうかは、どのログ バックアップに目的の復旧ポイントが含まれているかによって、次のように異なります。  
  
    -   復旧ポイントが障害の発生時点である場合は、最後に復元したデータ バックアップ (完全バックアップまたは差分バックアップ) 以降に作成されたすべてのログ バックアップを復元する必要があります。 詳細については、「[トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)」を参照してください。  
  
    -   特定の時点への復元の場合は、最新のログ バックアップを復元する必要がないことがあります。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用する場合、データベース復旧アドバイザーによって、指定された時点に復元するために必要なバックアップだけが選択されます。 これらのバックアップは、特定の時点への復元用として推奨される復元プランを示しています。 詳細については、「[SQL Server データベースを特定の時点に復元する &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)」を参照してください。  
  
## <a name="restarting-a-restore-sequence"></a>復元シーケンスの再実行  
 復元シーケンスの結果に問題がある場合、復元シーケンスを停止し、最初から再実行することができます。 たとえば、誤ってログ バックアップを多く復元しすぎて、目的の復旧ポイントを超えてしまった場合は、目的の復旧ポイントを含むログ バックアップまでの復元シーケンスを再実行する必要があります。  
  
## <a name="see-also"></a>参照  
 [バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [復元と復旧の概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [データベースの全体復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [オンライン復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [ファイル復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [ページ復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-pages-sql-server.md)   
 [段階的な部分復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  