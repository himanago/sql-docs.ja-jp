---
title: DBMS ベースのドライバー診断の例 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0485ecf720cb84580c17c77b31fc6816de2e679a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622270"
---
# <a name="dbms-based-driver-diagnostic-example"></a>DBMS ベースのドライバー診断の例
DBMS ベースのドライバーでは、DBMS に要求を送信し、アプリケーション、ドライバー マネージャーを使用する情報を返します。 書式設定しの引数を返しますが、ドライバーは、ドライバー マネージャーとのインターフェイスのコンポーネントであるため**SQLGetDiagRec**します。  
  
 たとえば、Oracle Rdb は、無効なカーソル名を検出しましたのは、SQL/サービス、Microsoft ドライバーを使用して、返されます次の値を**SQLGetDiagRec**:。  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 ドライバーで、エラーが発生したため、そのプレフィックスに追加、診断メッセージ ([Microsoft]) のベンダーとドライバー ([ODBC Rdb Driver])。  
  
 ドライバー可能性があります書式を設定しから次の値を返す場合は、DBMS では、従業員テーブルが見つかりませんでした、 **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 データ ソースで、エラーが発生したため、ドライバーは、診断メッセージをデータ ソース識別子 ([Rdb]) のプレフィックスを追加します。 ドライバーがデータ ソースと接続するコンポーネントであるために、診断メッセージにその仕入先 ([Microsoft]) および ([ODBC Rdb Driver]) の識別子のプレフィックスが追加されます。
