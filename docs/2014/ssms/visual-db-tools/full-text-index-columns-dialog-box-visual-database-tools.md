---
title: '[フルテキスト インデックスの列] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b4a01c8f5ca0230207c6b4ebbc4fc76244ea16f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165683"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a>[フルテキスト インデックスの列] ダイアログ ボックス (Visual Database Tools)
  このダイアログ ボックスには、テーブル デザイナーで開いたテーブルのテキスト インデックスに含まれる列が一覧表示されます。 このダイアログ ボックスにアクセスするには、テーブル デザイナーのテーブルを右クリックして **[フルテキスト インデックス]** を選択すると表示される **[フルテキスト インデックス]** ダイアログ ボックスで、表示または編集する列のインデックスをクリックし、右のグリッドの **[列]** フィールドをクリックして、省略記号 (**[...]**) をクリックします。  
  
## <a name="options"></a>および  
 **列**  
 フルテキスト インデックスに指定されている列の名前を表示します。 列を追加するには、最初の空のセルの中をクリックし、ドロップダウン リストから列を選択します。 テキスト ベースのデータ型の列または画像データ型の列だけが選択できます。  
  
 **[データ型]**  
 各列のデータ型を表示します。 これは、読み取り専用プロパティです。 データ型を変更するには、テーブル デザイナーでテーブルを開き、列をクリックして、 **[列のプロパティ]** タブでデータ型を編集します。  
  
 **[列による型付け]**  
 データ型が `image` の列だけに適用されます。 ドロップダウン リストが表示され、現在の列のデータ型を表す他の列のデータ型を選択できます。 現在の列が `image` データ型でない場合、値は [なし] になります。  
  
 データ型が `image` の列は、Microsoft Office ファイル (.doc、.xls、および .ppt ファイル)、テキスト ファイル (.txt ファイル)、HTML ファイル (.htm ファイル) を格納でき、その列のデータ型を image に設定することで、ファイルの中身を検索するフルテキスト検索ができるようになります。  
  
 **言語**  
 使用できる言語を一覧表示します。 列データに適した言語をドロップダウン リストから選択してください。 たとえば、英語のオペレーティング システムを使用している場合に、ドイツ語のテキストを含む列にインデックスを設定するときは、ドロップダウン リストからドイツ語を選択することによりインデックスのパフォーマンスが向上します。  
  
 **[統計的セマンティクス]**  
 選択されている列に対するセマンティック インデックスを有効にするかどうかを選択します。 詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../../relational-databases/search/semantic-search-sql-server.md)」を参照してください。  
  
 **[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、**[統計的セマンティクス]** チェック ボックスは無効になります。 **[言語]** を選択する前に **[統計的セマンティクス]** を選択した場合、ドロップダウン コンボ ボックスで使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。  
  
## <a name="see-also"></a>参照  
 [[フルテキスト インデックス] ダイアログ ボックス (Visual Database Tools)](visual-database-tools.md)  
  
  