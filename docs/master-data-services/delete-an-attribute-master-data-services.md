---
title: "属性を削除する (マスター データ サービス) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1d36564680430b7d35c415e23586c7fd0c47e084
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="delete-an-attribute-master-data-services"></a>属性を削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で、属性とそれに関連付けられたすべての属性値を完全に削除するには、属性を削除します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-delete-an-attribute"></a>属性を削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデルの管理]** ページでグリッドからモデルを選択し、 **[エンティティ]**をクリックします。  
  
3.  **[エンティティの管理]** ページで、属性を作成するエンティティの行を選択します。  
  
4.  **[属性]**をクリックします。  
  
5.  **[属性の管理]** ページで、次のいずれかの操作を行います。  
  
    -   属性の対象がリーフ メンバーの場合、 **[メンバーの種類]** ボックスの一覧から **[リーフ]** を選択します。  
  
    -   属性の対象が統合メンバーの場合、 **[メンバーの種類]** ボックスの一覧から **[統合]** を選択します。  
  
    -   属性の対象がコレクションの場合、 **[メンバーの種類]** ボックスの一覧から **[コレクション]** を選択します。  
  
6.  削除する属性の行を選択します。  
  
    > [!NOTE]  
    >  Name 属性または Code 属性を削除することはできません。  
  
7.  **[削除]**をクリックします。  
  
8.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [属性と #40 です。マスター データ サービスと #41 です。](../master-data-services/attributes-master-data-services.md)   
 [ドメイン ベースの属性と #40 です。マスター データ サービスと #41 です。](../master-data-services/domain-based-attributes-master-data-services.md)   
 [テキスト属性 (& r) #40 です。マスター データ サービスと #41 です。](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [ドメイン ベースの属性 (& r) #40 です。マスター データ サービスと #41 です。](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  