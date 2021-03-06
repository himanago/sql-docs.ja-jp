---
title: '代替方法: SQL ステートメントの使用 |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b95e6f0bd2b702080b3580b8b9eeb80ac5b06e8d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674260"
---
# <a name="alternatives-using-sql-statements"></a>他の方法: SQL ステートメントを使用する
ADO では、その組み込みプロパティとデータを編集するためのメソッドの代わりに、コマンドを使用してもできます。 プロバイダーによっては、このセクションで説明されているすべての操作することもできます、データ ソースにコマンドを渡すことによって。 SQL UPDATE ステートメントを使用してを使用せずにデータを変更するなど、**値**のプロパティを**フィールド**します。 SQL の INSERT ステートメントは、ADO メソッドではなく、データ ソースに新しいレコードを追加するために使用できます**AddNew**します。 SQL またはプロバイダーのデータ操作言語の詳細については、データ ソースのドキュメントを参照してください。  
  
 たとえば、次のコードに示すように、データベースへの DELETE ステートメントを含む SQL 文字列を渡すことができます。  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
