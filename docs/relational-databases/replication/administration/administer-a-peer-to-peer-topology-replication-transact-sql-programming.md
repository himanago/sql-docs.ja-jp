---
title: "ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, peer-to-peer replication
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c4ee67601036ff703687015ae3b4b89c822f7054
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="administer-a-peer-to-peer-topology-replication-transact-sql-programming"></a>ピア ツー ピア トポロジの管理 (レプリケーション Transact-SQL プログラミング)
  ピア ツー ピア トポロジの管理は通常のトランザクション レプリケーション トポロジの管理と似ていますが、特別な考慮が必要な部分が数多くあります。 ピア ツー ピア トポロジの管理が通常のトポロジ管理と最も異なる点は、ある種の変更を行うときにシステムを *停止*する必要があることです。 システムを停止するときには、すべてのノードでパブリッシュ済みテーブルの利用を停止し、各ノードが他のすべてのノードの変更を受け取っていることを確認します。 詳細については、「[レプリケーション トポロジの停止 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)」を参照してください。  
  
> [!NOTE]  
>  ピア ツー ピア トポロジでは、ディストリビューターはプル サブスクライバーより前の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンを使用できません。  
  
### <a name="to-add-an-article-to-an-existing-configuration"></a>既存の構成にアーティクルを追加するには  
  
1.  システムを停止します。  
  
2.  トポロジ内の各ノードでディストリビューション エージェントを停止します。 詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)」または「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」を参照してください。  
  
3.  CREATE TABLE ステートメントを実行して、トポロジ内の各ノードに新しいテーブルを追加します。  
  
4.  [bcp ユーティリティ](../../../tools/bcp-utility.md)を使用して、全ノードの新しいテーブルにデータを一括コピーします。  
  
5.  [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) を実行して、トポロジ内の各ノードに新しいアーティクルを作成します。 詳細については、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」を参照してください。  
  
    > [!NOTE]  
    >  [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) の実行後、レプリケーションによってトポロジ内のサブスクリプションにアーティクルが自動的に追加されます。  
  
6.  トポロジ内の各ノードでディストリビューション エージェントを再起動します。  
  
### <a name="to-make-schema-changes-to-a-publication-database"></a>パブリケーション データベースのスキーマを変更するには  
  
1.  システムを停止します。  
  
2.  データ定義言語 (DDL) ステートメントを実行して、パブリッシュ済みテーブルのスキーマを変更します。 サポートされるスキーマ変更の詳細については、「[パブリケーション データベースでのスキーマの変更](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
3.  パブリッシュ済みテーブルの利用を再開する前に、再びシステムを停止します。 これにより、新しいデータ変更がレプリケートされる前に、すべてのノードでスキーマ変更が受け取られます。  
  
## <a name="example"></a>例  
 次の例は、2 つのノードを持つ既存のピア ツー ピア レプリケーション トポロジに新しいテーブル アーティクルを追加する方法を示しています。  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_1.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_2.sql)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../relational-databases/replication/codesnippet/tsql/administer-a-peer-to-pee_3.sql)]  
  
## <a name="see-also"></a>参照  
 [管理 (レプリケーション)](../../../relational-databases/replication/administration/administration-replication.md)   
 [SQL Server データベースのバックアップと復元](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [ピア ツー ピア トランザクション レプリケーション](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  