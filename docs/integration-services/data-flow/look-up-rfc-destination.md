---
title: "RFC 転送先を参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c9db6a056a69d502b4a93b9575cb565da798adf
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="look-up-rfc-destination"></a>[RFC 転送先の参照]
  SAP Netweaver BW システムで定義された RFC 転送先を参照する場合、 **[RFC 転送先の参照]** ダイアログ ボックスを使用します。 使用できる RFC 転送先の一覧が表示されたら目的の転送先を選択すると、関連するオプションに必要な値が設定されます。  
  
 SAP BW 変換元と SAP BW 変換先は両方とも、 **[RFC 転送先の参照]** ダイアログ ボックスを使用します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW のコンポーネントの詳細については、「 [SAP BW Source](../../integration-services/data-flow/sap-bw-source.md) 」(SAP BW 変換元) および「 [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md)」(SAP BW 変換先) を参照してください。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
 **[RFC 転送先の参照] ダイアログ ボックスを開くには**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換元または変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、SAP BW 変換元または変換先をダブルクリックします。  
  
3.  **[SAP BW 変換元エディター]** または **[SAP BW 変換先エディター]**で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。  
  
4.  **[接続マネージャー]** ページの **[RFC 転送先]** で、 **[参照]** をクリックして **[RFC 転送先の参照]** ダイアログ ボックスを表示します。  
  
     **[SAP BW 変換元エディター]**で、 **[RFC 転送先]** は、 **[実行モード]** の値が **[P - プロセス チェーンをトリガー]** または **[W - 通知を待機]**である場合にのみ表示されます。  
  
## <a name="options"></a>オプション  
 **転送先**  
 SAP Netweaver BW システムで定義された RFC 転送先の名前を表示します。  
  
 **ゲートウェイ ホスト**  
 ゲートウェイ ホストのサーバー名または IP アドレスを表示します。 通常、IP アドレスの名前は、SAP アプリケーション サーバーの名前と同じです。  
  
 **ゲートウェイ サービス**  
 **NN**がシステム数である、 **sapgwNN** という形式でゲートウェイ サービスの名前を表示します。  
  
 **プログラム ID**  
 RFC 転送先に関連付けられているプログラム ID を表示します。  
  
## <a name="see-also"></a>参照  
 [SAP bw 変換元エディターと &#40; です。接続マネージャー」 ページと &#41; です。](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [SAP BW 変換先エディター &#40;[接続マネージャー] ページ&#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)   
 [Microsoft Connector for SAP BW の F1 ヘルプ](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  