---
title: 相互運用性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d5e4fbee458bec88461d3e2945a466c848d3345
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794124"
---
# <a name="interoperability"></a>相互運用性
*相互運用性*は多くのさまざまな Dbms で動作する単一のアプリケーションの機能です。 ジェネリック、相互運用可能なアプリケーションを記述する必要は、ODBC の開発につながる大きな要因の 1 つでした。 ただし、相互運用性はありません「いない相互運用性」の後に、単純なパスを「完全に相互運用可能な」。 パスは多数の分岐を備え、各機能、速度、コードの複雑さ、および開発にかかる時間の間でトレードオフが必要です。  
  
 相互運用可能なアプリケーションを作成するプロセスでは、いくつかの手順に従います。  
  
1.  アプリケーションで ODBC を使用しているかどうかを決定します。  
  
2.  上のトレードオフは、そのレベルに到達するために必要な決定の相互運用性のレベルを選択します。  
  
3.  相互運用可能なコードを記述して、できるだけ完全にテストします。  
  
 相互運用性が主に、アプリケーションの作成者のドメインであることに注意してください。 ドライバーは、1 つの DBMS で使用できる、定義上は相互運用可能なではありません。 正しく実装し、1 つの DBMS 上の ODBC の公開の相互運用性で、役割を果たします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC が正解ですか?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [相互運用性のレベルの選択](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [ターゲット DBMS とドライバーの決定](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [使用するデータベース機能の検討](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [製品サイクルの長さ](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [相互運用可能なアプリケーションの作成](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [相互運用可能なアプリケーションのテスト](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
