---
title: Microsoft Naive Bayes アルゴリズム テクニカル リファレンス |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 900da37bf40f22f039146dfeb8219930b8661887
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34015889"
---
# <a name="microsoft-naive-bayes-algorithm-technical-reference"></a>Microsoft Naive Bayes アルゴリズム テクニカル リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で予測モデリング用に提供されている分類アルゴリズムです。 このアルゴリズムでは、各列に依存関係がないと仮定して、入力列と予測可能列の条件付き確率が計算されます。 この非依存性の仮定が、Naive Bayes という名前の由来です。  
  
## <a name="implementation-of-the-microsoft-naive-bayes-algorithm"></a>Microsoft Naive Bayes アルゴリズムの実装  
 このアルゴリズムは、他の [!INCLUDE[msCoName](../../includes/msconame-md.md)] アルゴリズムよりも計算量が少ないので、入力列と予測可能列のリレーションシップを見つけるためのマイニング モデルを短時間で生成できます。 このアルゴリズムは、入力属性値と出力属性値の各ペアを考慮します。  
  
 Bayes の定理については、このドキュメントでは説明しません。詳細については、Microsoft Research の「[ベイジアン ネットワークの学習: 知識と統計データの組み合わせ](http://go.microsoft.com/fwlink/?LinkId=207029)」を参照してください。  
  
 すべてのモデルにおいて可能性のある不足値を考慮するように確率を調整する方法については、「[Missing Values &#40;Analysis Services - Data Mining&#41;](../../analysis-services/data-mining/missing-values-analysis-services-data-mining.md)」(不足値 &#40;Analysis Services - データ マイニング&#41;) を参照してください。  
  
### <a name="feature-selection"></a>機能の選択  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、モデルを構築するときに考慮される値の数を制限するための自動的な機能選択が行われます。 詳細については、「[機能の選択 &#40;データ マイニング&#41;](../../analysis-services/data-mining/feature-selection-data-mining.md)」を参照してください。  
  
|アルゴリズム|分析の方法|コメント|  
|---------------|------------------------|--------------|  
|Naive Bayes|Shannon のエントロピ<br /><br /> K2 事前分布を指定したベイズ定理<br /><br /> 均一な事前分布を指定したベイズ ディリクレ等式 (既定値)|Naive Bayes で使用できる属性は、不連続属性と分離された属性だけです。したがって、興味深さのスコアは使用できません。|  
  
 このアルゴリズムは、処理時間が最短になり、最も重要な属性を効率よく選択できるように設計されています。ただし、次のようにパラメーターを設定することで、アルゴリズムが使用するデータを制御できます。  
  
-   入力として使用される値を制限するには、MAXIMUM_INPUT_ATTRIBUTES の値を小さくします。  
  
-   モデルで分析される属性の数を制限するには、MAXIMUM_OUTPUT_ATTRIBUTES の値を小さくします。  
  
-   任意の 1 つの属性について考慮できる値の数を制限するには、MINIMUM_STATES の値を小さくします。  
  
## <a name="customizing-the-naive-bayes-algorithm"></a>Naive Bayes アルゴリズムのカスタマイズ  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、結果として得られるマイニング モデルの動作、パフォーマンス、および精度に影響を与えるいくつかのパラメーターがサポートされています。 モデル列にモデリング フラグを設定してデータの処理方法を制御することも、マイニング構造にフラグを設定して不足値または NULL 値の処理方法を指定することもできます。  
  
### <a name="setting-algorithm-parameters"></a>アルゴリズム パラメーターの設定  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、結果として得られるマイニング モデルのパフォーマンスおよび精度に影響を与えるいくつかのパラメーターがサポートされています。 次の表では、各パラメーターについて説明します。  
  
 *MAXIMUM_INPUT_ATTRIBUTES*  
 選択した機能を呼び出す前にアルゴリズムが処理できる入力属性の最大数を指定します。 この値を 0 に設定すると、入力属性に対する機能の選択が無効になります。  
  
 既定値は 255 です。  
  
 *MAXIMUM_OUTPUT_ATTRIBUTES*  
 選択した機能を呼び出す前にアルゴリズムが処理できる出力属性の最大数を指定します。 この値を 0 に設定すると、出力属性に対する機能の選択が無効になります。  
  
 既定値は 255 です。  
  
 *MINIMUM_DEPENDENCY_PROBABILITY*  
 入力属性と出力属性間の依存関係の最小確率を指定します。 この値は、アルゴリズムによって生成されるコンテンツのサイズを制限するために使用されます。 このプロパティは 0 ～ 1 の範囲で設定できます。 値を大きくすると、モデルのコンテンツの属性数が減ります。  
  
 既定値は 0.5 です。  
  
 *MAXIMUM_STATES*  
 アルゴリズムによってサポートされる属性状態の最大数を指定します。 属性の状態の数が状態の最大数よりも大きい場合、アルゴリズムでは属性の最も一般的な状態が使用され、残りの状態は存在しないものとして処理されます。  
  
 既定値は、100 です。  
  
### <a name="modeling-flags"></a>ModelingFlags  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムでは、次のモデリング フラグがサポートされています。 モデリング フラグは、マイニング構造やマイニング モデルを作成するときに定義し、分析時に各列の値をどのように処理するかを指定します。 詳細については、「[モデリング フラグ &#40;データ マイニング&#41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)」を参照してください。  
  
|モデリング フラグ|Description|  
|-------------------|-----------------|  
|MODEL_EXISTENCE_ONLY|列が、Missing および Existing の 2 つの可能な状態を持つ列として扱われることを示します。 NULL は Missing 値になります。<br /><br /> マイニング モデル列に適用されます。|  
|NOT NULL|列に NULL を含めることはできないことを示します。 モデルのトレーニング中に NULL が検出された場合はエラーが発生します。<br /><br /> マイニング構造列に適用されます。|  
  
## <a name="requirements"></a>必要条件  
 Naive Bayes ツリー モデルには、キー列、少なくとも 1 つの予測可能属性、および少なくとも 1 つの入力属性が必要です。 属性を連続にすることはできません。データに連続する数値データが含まれる場合は、無視または分離されます。  
  
### <a name="input-and-predictable-columns"></a>入力列と予測可能列  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、次の表に示す特定の入力列と予測可能列がサポートされています。 マイニング モデルにおけるコンテンツの種類の意味については、「[コンテンツの種類 &#40;データ マイニング&#41;](../../analysis-services/data-mining/content-types-data-mining.md)」を参照してください。  
  
|列|コンテンツの種類|  
|------------|-------------------|  
|入力属性|Cyclical、Discrete、Discretized、Key、Table、Ordered|  
|予測可能な属性|Cyclical、Discrete、Discretized、Table、Ordered|  
  
> [!NOTE]  
>  コンテンツの種類 Cyclical および Ordered はサポートされますが、アルゴリズムはこれらを不連続の値として扱い、特別な処理は行いません。  
  
## <a name="see-also"></a>参照  
 [Microsoft Naive Bayes アルゴリズム](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)   
 [Naive Bayes モデルのクエリ例](../../analysis-services/data-mining/naive-bayes-model-query-examples.md)   
 [Naive Bayes モデル & #40; のマイニング モデル コンテンツAnalysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
