---
title: UPDATE、DELETE、および INSERT ステートメント |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92fb7b0e9722c52c7f1e9fc071d434f531b2fc46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721910"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE、DELETE、INSERT ステートメント
SQL ベースのアプリケーションでは、テーブルに変更を加えるを実行して、 **UPDATE**、**削除**、および**挿入**ステートメント。 これらのステートメントでは、Minimum SQL 文法の準拠レベルの一部であるし、すべてのドライバーとデータ ソースでサポートする必要があります。  
  
 これらのステートメントの構文です。  
  
 **UPDATE**  *table-name*  
  
 **設定***列識別子* **=** {*式*&#124; です。**NULL**}  
  
 [**、** *列識別子* **=** {*式*&#124; です。**NULL**}].  
  
 [**WHERE** *search-condition*]  
  
 **DELETE FROM** *table-name*[**WHERE** *search-condition*]  
  
 **INSERT INTO** *table-name*[**(***column-identifier* [**,** *column-identifier*]...**)**]  
  
 {*クエリ仕様* &#124; **値 (* * * 挿入値*[* *、** *挿入値*].**)**}  
  
 なお、*クエリ仕様*要素は、コアと拡張 SQL 文法とでのみ有効ですが、*式*と*検索条件*要素の詳細になりますコアと拡張 SQL 文法で複雑です。  
  
 などの他の SQL ステートメント**更新**、**削除**と**挿入**ステートメントは、多くの場合は詳細はパラメーターを使用するときに効率的です。 たとえば、次のステートメントを準備および Orders テーブルに複数の行を挿入するために繰り返し実行します。  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 この効率性のパラメーター値の配列を渡すことによって増やすことができます。 ステートメントのパラメーターとパラメーター値の配列の詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)します。
