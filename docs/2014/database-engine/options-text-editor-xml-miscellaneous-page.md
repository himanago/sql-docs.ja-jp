---
title: オプション (テキスト エディター - XML - その他 ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2a87635bedba24e440dd2d6c5b7a2c48c7408a9d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126672"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a>[オプション] ([テキスト エディター]/[XML]/[その他] ページ)
  **[オプション]** ダイアログ ボックスを使用すると、XML エディターのオートコンプリートとスキーマの設定を変更できます。 この設定を変更するには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[テキスト エディター]** フォルダーを展開して、 **[XML]** 、 **[その他]** の順にクリックします。  
  
## <a name="auto-insert"></a>[自動挿入]  
 **終了タグ**  
 テキスト エディターで XML 要素を記述する際に、終了タグが自動的に追加されます。 要素の開始タグが選択されると、対応する終了タグが挿入されます。この場合、対応する名前空間プレフィックスも含められます。 既定では、このチェック ボックスはオンになっています。  
  
 **属性の引用符**  
 XML 属性を記述する際に、自動的に `="``"` が挿入され、カレット (**^** ) が引用符の内側に置かれます。 既定では、このチェック ボックスはオンになっています。  
  
 **Namespace 宣言**  
 名前空間の宣言が必要な場所には、自動的に宣言が挿入されます。 既定では、このチェック ボックスはオンになっています。  
  
 **その他のマークアップ (コメント、CDATA)**  
 コメント、CDATA、DOCTYPE、処理命令、その他のマークアップがオートコンプリートされます。 既定では、このチェック ボックスはオンになっています。  
  
## <a name="network"></a>ネットワーク  
 **Dtd とスキーマを自動的にダウンロードします。**  
 スキーマと DTD (Document Type Definition) は HTTP ロケーションから自動的にダウンロードされます。 この機能では、自動プロキシ サーバー検出が有効な System.Net を使用します。 既定では、このチェック ボックスはオンになっています。  
  
## <a name="outlining"></a>[アウトライン]  
 **ファイルを開いたときにアウトライン モードを入力します**  
 ファイルが開いているときにアウトライン機能をオンにします。 既定では、このチェック ボックスはオンになっています。  
  
## <a name="caching"></a>キャッシュ  
 **スキーマ**  
 スキーマ キャッシュの場所を指定します。 [...] ボタンをクリックすると、現在のスキーマ キャッシュの場所が新しいウィンドウに表示されます。 既定の場所は *\<Management Studio install directory >* \Xml\Schemas です。  
  
  
