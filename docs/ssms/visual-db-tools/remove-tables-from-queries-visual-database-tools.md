---
title: "クエリからのテーブルの削除 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 726f169be56f64484d505b91ca5d93a6426cbf7c
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="remove-tables-from-queries-visual-database-tools"></a>クエリからのテーブルの削除 (Visual Database Tools)
クエリからテーブルまたはテーブル値オブジェクトを削除できます。  
  
> [!NOTE]  
> テーブルまたはテーブル値オブジェクトを削除しても、現在のクエリから削除されるだけです。データベースからは何も削除されません。 データベースからテーブルを削除する方法については、「 [データベースからテーブルを削除する方法 (Visual Database Tools)](http://msdn.microsoft.com/en-us/ca6aa3e9-9885-44c3-bafc-aec441fd97ec)」を参照してください。  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>テーブルまたはテーブル構造オブジェクトを削除するには  
  
-   **ダイアグラム ペイン**で、テーブル、ビュー、ユーザー定義関数、シノニム、またはクエリを選択し、Del キーを押すか、オブジェクトを右クリックして、表示されるダイアログ ボックスの **[削除]** をクリックします。 同時に複数のオブジェクトを選択して削除することもできます。  
  
    または  
  
-   **SQL ペイン**でオブジェクトへのすべての参照を削除します。  
  
テーブルまたはテーブル値オブジェクトを削除すると、クエリおよびビュー デザイナーでは、そのテーブルまたはテーブル値オブジェクトを含む結合が自動的に削除され、これらのオブジェクトの列に対する参照も **SQL ペイン** および **抽出条件ペイン**から自動的に削除されます。 ただし、オブジェクトを含む複合式がクエリに含まれる場合、オブジェクトに対する参照がすべて削除されるまで、オブジェクトが自動的に削除されることはありません。  
  
## <a name="see-also"></a>参照  
[クエリへのテーブルの追加 (Visual Database Tools)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[テーブルの別名の作成 (Visual Database Tools)](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md)  
[検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[クエリ結果の要約 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
