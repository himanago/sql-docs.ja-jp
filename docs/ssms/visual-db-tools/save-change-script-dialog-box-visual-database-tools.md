---
title: "[変更スクリプトの保存] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ad99676eff79f7cc2fbb078278d0aeb4cf253102
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>[変更スクリプトの保存] ダイアログ ボックス (Visual Database Tools)
このダイアログ ボックスには、最後にテーブルを保存してから、変更を行った [!INCLUDE[tsql](../../includes/tsql_md.md)] スクリプトが表示されます。 選択した場所に、テキスト ファイル形式でスクリプトを保存することもできます。  
  
テーブル デザイナーのテーブルへの変更を保存しなかった場合に、このダイアログ ボックスにアクセスできます。 **[テーブル デザイナー]** メニューの **[変更スクリプトの生成]**をクリックします。  
  
> [!NOTE]  
> Visual Database Tools によって提供される変更スクリプトにはエラー処理は含まれていません。 ツールが開いた後でデータベース オブジェクトが変更されていないことを前提としているため、変換関連の問題が発生することを想定していません。 変更スクリプトを実行する前に、適切なエラー処理ステートメントを含める必要があります。  
  
## <a name="options"></a>オプション  
**[保存時に変更スクリプトを自動作成する]**  
オンにすると、テーブルへの変更を保存するときに毎回 **[変更スクリプトの保存]** ダイアログ ボックスが表示されるようになります。  
  
**可**  
テキスト ファイルの場所を選択できる **[上書き保存]** ダイアログ ボックスを呼び出します。  
  
**いいえ**  
変更スクリプトの作成を取り消します。  
  
