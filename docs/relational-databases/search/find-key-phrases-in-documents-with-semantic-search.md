---
title: "セマンティック検索を使用したドキュメント内のキー フレーズの検索 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6c005c3de0b3cd1e8e5562c038321a53e04da38a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>セマンティック検索を使用したドキュメント内のキー フレーズの検索
  統計的セマンティック インデックス作成用に構成されたドキュメントまたはテキスト列内のキー フレーズのクエリを実行する方法について説明します。  

##  <a name="howtofind"></a> SEMANTICKEYPHRASETABLE を使用してドキュメント内のキー フレーズを検索する  
 特定のドキュメントに含まれるキー フレーズや特定のキー フレーズを含むドキュメントを識別するには、[semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md) 関数を使用してクエリを実行します。  
  
 SEMANTICKEYPHRASETABLE は、指定されたテーブル内の列に関連付けられているこれらのキー フレーズに対し、0 行以上の行を含むテーブルを返します。 この行セット関数は、標準のテーブル名のように、SELECT ステートメントの FROM 句で参照できます。  
  
> [!NOTE]  
>  このリリースでは、セマンティック検索のためにインデックスが作成されるのは 1 つの単語のみです。複数の単語で構成されるフレーズ (ngrams) のインデックスは作成されません。 また、1 つの単語のさまざまな形式は個別にインデックスが付けられます。たとえば、「computer」と「computers」は個別にインデックスが作成されます。  
  
 SEMANTICKEYPHRASETABLE 関数に必要なパラメーターの詳細や関数から返される結果のテーブルについては、[semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md) のトピックを参照してください。  
  
> [!IMPORTANT]  
>  対象の列では、フルテキスト インデックスとセマンティック インデックスが有効になっている必要があります。  
  
###  <a name="HowToTopPhrases"></a> 例 1: 特定のドキュメントに含まれる上位のキー フレーズを見つける  
 次の例では、AdventureWorks サンプル データベースの Production.Document テーブルの Document 列にある、@DocumentId 変数で指定されたドキュメントから、上位 10 個のキー フレーズを取得します。 @DocumentId 変数は、フルテキスト インデックスのキー列の値を表します。  
  
```tsql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 **SEMANTICKEYPHRASETABLE** 関数は、テーブル スキャンではなくインデックス シークを使用してこれらの結果を効率的に取得します。  
  
###  <a name="HowToTopDocuments"></a> 例 2: 特定のキー フレーズを含む上位のドキュメントを見つける  
 次の例では、AdventureWorks サンプル データベースの Production.Document テーブルの Document 列から、キー フレーズ “Bracket” を含む上位 25 個のドキュメントを取得します。  
  
```tsql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  