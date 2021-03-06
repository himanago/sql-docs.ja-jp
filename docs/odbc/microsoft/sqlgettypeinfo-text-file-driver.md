---
title: SQLGetTypeInfo (テキスト ファイル ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c1c38b66e9b8a3c1cbed4a3712f7af866935089
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847730"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 によって生成されたテーブルの型 (TYPE_NAME) の名前が返される**SQLGetTypeInfo**データ ソースで最もよく使用する名前になります。  
  
 SQL_ALL_EXCEPT_LIKE が返されます、検索可能な列で、バイトのカウンター、Double、1 つ、Long、Short データ型。 (LIKE 機能は、値を比較を実行し、ODBC 標準変換関数を使用する文字に変換することで実現できます)。  
  
 テキストのドライバーを使用すると、 **SQLGetTypeInfo** CASE_SENSITIVE の値が FALSE のテキストのデータ型 (CHAR および LONGCHAR) を返しますとデータ型実際には、大文字小文字を区別します。
