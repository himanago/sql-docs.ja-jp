---
title: スクロール可能なカーソル |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 2c8a5f50-9b37-452f-8160-05f42bc4d97e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70d02b933104a3106d95f6760cbdcf0abb347716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791558"
---
# <a name="scrollable-cursors"></a>スクロール可能なカーソル
最新のスクリーン ベースのアプリケーションでは、ユーザーは、データを前後をスクロールします。 このようなアプリケーションでは、問題は、以前にフェッチした行を返します。 1 つの方法としてを終了し、カーソルを閉じて、カーソルが必要な行に達するまで行をフェッチします。 結果セットを読み取り、ローカルにキャッシュ、およびアプリケーションでのスクロールを実装する可能性もあることです。 両方の可能性が、小さな結果セットにのみ使用して、後者の可能性としては実装も困難です。 優れたソリューションが使用するには、*スクロール可能なカーソル、* 後ろに移動し、結果セットに転送することができます。  
  
 A*スクロール可能なカーソル*をユーザーがスクロール前後へデータを最新のスクリーン ベースのアプリケーションでよく使用されます。 ただし、アプリケーション使用はスクロール可能なカーソル順方向専用カーソルが、ジョブを実行していない場合にのみスクロール可能なカーソルは順方向専用カーソルより通常高価です。  
  
 後方に移動する機能が順方向専用カーソルには該当しません質問を発生させます。 スクロール可能なカーソルが以前にフェッチされた行に加えられた変更を検出する必要がありますか。 更新、削除、および新しく挿入された行を検出する必要がありますか。  
  
 結果の定義を設定するために、この質問が発生: 特定の条件に一致する行のセットなど、その条件に一致するかどうかも、状態が表示する行をチェックするときに記載されていないかどうか行含める必要があります、同じデータがフェッチされるたびに。 前者の省略を使うと、スクロール可能なカーソルの行が挿入または削除され、後者は、更新されたデータを検出するかどうかを検出します。  
  
 変更を検出する機能が場合があります。、便利な場合があります。 たとえば、会計アプリケーションには、カーソルをすべての変更を無視する必要があります。ブックの「分散では、可能な場合、カーソルは、最新変更を示しています。 一方で、航空券予約システムが、カーソルは、データを最新の変更を表示する必要があります。このようなカーソルなしは、最新のフライトの可用性を表示するデータベースを継続的に再クエリする必要があります。  
  
 さまざまなアプリケーションのニーズをカバーするには、は、ODBC は、4 種類のスクロール可能なカーソルを定義します。 これらのカーソルでは、経費の両方を異なるし、結果の変更を検出する機能に設定します。 スクロール可能なカーソルが行への変更を検出できる場合のみを検出できるにそれらの行を更新しようとしたときに注意してください。現在フェッチされた行への変更がカーソルに通知するデータ ソースの方法はありません。 変更の可視性をトランザクション分離レベルによっても制御にも注意してください。詳細については、次を参照してください。[トランザクション分離](../../../odbc/reference/develop-app/transaction-isolation.md)します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [スクロール可能なカーソルの種類](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [スクロール可能なカーソルの使用](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [相対と絶対のスクロール](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [ブックマーク](../../../odbc/reference/develop-app/bookmarks-odbc.md)
