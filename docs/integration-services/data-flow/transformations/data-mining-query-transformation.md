---
title: "データ マイニング クエリ変換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataminingquerytrans.f1
- sql13.dts.designer.dmquerytransformation.miningmodel.f1
- sql13.dts.designer.dmquerytransformation.query.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4b557efa62075f7b88e6b70cf5950546444b95d8
ms.openlocfilehash: 7ec5d0d1168e49fb38ce8b58eaa75d6c0d6c51b5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/19/2017

---
# <a name="data-mining-query-transformation"></a>データ マイニング クエリ変換
  データ マイニング クエリ変換は、データ マイニング モデルに対して予測クエリを実行します。 この変換には、データ マイニング拡張機能 (DMX) クエリを作成するためのクエリ ビルダーが含まれています。 このクエリ ビルダーを使用すると、DMX 言語を使用して、既存のマイニング モデルに対して変換入力データを評価する、カスタム ステートメントを作成できます。 詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](../../../dmx/data-mining-extensions-dmx-reference.md)」を参照してください。  
  
 同じデータ マイニング構造で複数のモデルが構築されている場合、1 回の変換で複数の予測クエリを実行することもできます。 詳細については、「 [データ マイニング クエリ ツール](../../../analysis-services/data-mining/data-mining-query-tools.md)」を参照してください。  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a>データ マイニング クエリ変換の構成  
 データ マイニング クエリ変換は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 接続マネージャーを使用して [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] プロジェクト、またはマイニング構造とマイニング モデルを含む [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスに接続します。 詳細については、「 [Analysis Services 接続マネージャー](../../../integration-services/connection-manager/analysis-services-connection-manager.md)」を参照してください。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="data-mining-query-transformation-editor-mining-model-tab"></a>[データ マイニング クエリ変換エディター]\ ([マイニング モデル] タブ)
  **[データ マイニング クエリ変換エディター]** ダイアログ ボックスの **[マイニング モデル]** タブを使用すると、データ マイニング構造とそのマイニング モデルを選択できます。  
  
### <a name="options"></a>オプション  
 **接続**  
 リスト ボックスを使用して既存の Analysis Services 接続を選択するか、以下に説明する **[新規作成]** ボタンを使用して新しい接続を作成します。  
  
 **[新規作成]**  
 **[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 **マイニング構造**  
 使用できるマイニング モデル構造の一覧から選択します。  
  
 **[マイニング モデル]**  
 選択したデータ マイニング構造に関連付けられているマイニング モデルの一覧を表示します。  
  
## <a name="data-mining-query-transformation-editor-query-tab"></a>[データ マイニング クエリ変換エディター]\ ([クエリ] タブ)
  **[データ マイニング クエリ変換エディター]** ダイアログ ボックスの **[クエリ]** タブを使用すると、予測クエリを作成できます。  
  
### <a name="options"></a>オプション  
 **[データ マイニング クエリ]**  
 データ マイニング拡張機能 (DMX) クエリを、テキスト ボックスに直接入力します。  
  
 **[新しいクエリの作成]**  
 **[新しいクエリの作成]** をクリックし、グラフィカルなクエリ ビルダーを使用して、データ マイニング拡張機能 (DMX) クエリを作成します。  
  
