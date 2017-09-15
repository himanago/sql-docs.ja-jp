---
title: "マージ テーブル アーティクルの処理順序の指定 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
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
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e84aea86e02abc3820ec615bbcfbe1c41a5cdfd7
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="specify-the-processing-order-of-merge-table-articles"></a>マージ テーブル アーティクルの処理順序の指定
  マージ レプリケーションでは、同期処理中にアーティクルをマージ エージェントで処理する順序を指定できます。 この順序は、レプリケーションのストアド プロシージャを使用して、アーティクル作成時に各アーティクルに対してプログラムから割り当てることができます。 アーティクルは、最も小さい値から最も大きい値の順序で処理されます。 2 つのアーティクルの値が同じ場合、それらは同時に処理されます。 詳細については、「[マージ アーティクルの処理順序の指定](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)」を参照してください。  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>新しいマージ アーティクルの処理順序を指定するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、[sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) を実行します。 アーティクルの処理順序を表す整数値を **@processing_order**」を参照してください。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
    > [!NOTE]  
    >  処理順序を指定してアーティクルを作成する場合は、アーティクルの順序を表す値の間に、ある程度の間隔を設けるようにしてください。 こうすることで、後で、新しい値を設定するときに作業が楽になります。 たとえば、処理順序を指定するアーティクルが 3 つある場合、 **@processing_order** の値を 1、2、3 とせずに、それぞれ、10、20、30 のように指定します。  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>マージ アーティクルの処理順序を変更するには  
  
1.  アーティクルの処理順序を指定するには、[sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) を実行し、結果セットの **processing_order** の値を確認します。  
  
2.  パブリッシャー側のパブリケーション データベースに対して、[sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) を実行します。 **@property** に **processing_order** の値を指定し、**@value** には処理順序を表す整数値を指定します。  
  
## <a name="see-also"></a>参照  
 [マージ アーティクルの処理順序の指定](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  