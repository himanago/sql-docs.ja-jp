---
title: "[SAP BW ソース エディター]\\ ([列] ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sapbwsource.columns.f1
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2047fddb6986bd3014015d742053bfb0dda42019
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="sap-bw-source-editor-columns-page"></a>[SAP BW ソース エディター]\ ([列] ページ)
  **[SAP BW 変換元エディター]** の **[列]** ページを使用すると、出力列をそれぞれの外部 (ソース) 列にマップできます。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換元コンポーネントの詳細については、「 [SAP BW 転送元](../../integration-services/data-flow/sap-bw-source.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
> [!IMPORTANT]  
>  SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。 これらの要件を確認するには、SAP にお問い合わせください。  
  
 **[列] ページを開く**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、SAP BW 変換元をダブルクリックします。  
  
3.  **[SAP BW 変換元エディター]**で、 **[列]** をクリックして **[列]** ページを開きます。  
  
## <a name="options"></a>オプション  
  
> [!NOTE]  
>  変換元を構成するために必要な値がわからない場合は、SAP 管理者に確認してください。  
  
 **使用できる外部列**  
 データ ソース内の使用可能な外部列の一覧を表示し、データ フローに含める列を選択します。  
  
 列をデータ フローに含めるには、列名のチェック ボックスをオンにします。 チェック ボックスをオンにする順序は、列が出力される順序を決定します。 つまり、オンにした最初のチェック ボックスは、最初の出力列、2 番目のチェック ボックスは 2 番目の出力列となります。  
  
 **外部列**  
 選択した外部 (ソース) 列を表示します。 選択した列は、この変換元からのデータを使用する下流コンポーネントを構成するときの表示順と同じ順序で表示されます。  
  
 列の順序を変更するには、 **[使用できる外部列]** の一覧で、すべての列のチェック ボックスをオフにします。 それから、表示したい順に列を選択します。  
  
 **出力列**  
 各出力列の一意な名前を表示します。 既定では選択された外部 (ソース) 列の名前です。 ただし、一意のわかりやすい名前を入力できます。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーが表示されます、 **出力列** このソースからデータを使用する下流コンポーネントを構成するときに列の名前。  
  
## <a name="see-also"></a>参照  
 [SAP BW 変換元エディター &#40;[接続マネージャー] ページ&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [SAP BW ソース エディター &#40;[エラー出力] ページ&#41;](../../integration-services/data-flow/sap-bw-source-editor-error-output-page.md)   
 [SAP bw 変換元エディターと &#40; です。「詳細」 ページと &#41; です。](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [Microsoft Connector for SAP BW の F1 ヘルプ](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  