---
title: "データ処理拡張機能の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], about extensions
ms.assetid: 1d652605-9313-4c75-98b4-ba4dcbbb222d
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 075724639c912f40c3ef7c49227ba653bd086fcd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="data-processing-extensions-overview"></a>データ処理拡張機能の概要
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能を使用することによって、データ ソースに接続し、データを取得できます。 データ処理拡張機能は、データ ソースとデータセット間のブリッジとしても機能します。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]データ処理拡張機能のサブセットと似ている、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]データ プロバイダーのインターフェイスです。  
  
 次の表は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] が備えているデータ処理拡張機能を示しています。  
  
|データ処理拡張機能|Description|  
|-------------------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 向けデータ処理拡張機能|.NET Framework Data Provider for SQL Server を使用して [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]と接続し、データを取得します。|  
|OLE DB 向けデータ処理拡張機能|OLE DB の .NET Framework データ プロバイダーを使用します。 この拡張機能を使用して、レポート サーバーは、OLE DB プロバイダーを持つすべてのデータ ソースをクエリできます。|  
|Oracle 向けデータ処理拡張機能|Oracle の .NET Framework データ プロバイダーを使用します。 この拡張機能を使用して、レポート サーバーは、Oracle クライアント接続ソフトウェアをとおして Oracle データ ソースにアクセスできます。|  
|ODBC 向けデータ処理拡張機能|ODBC 用の .NET Framework データ プロバイダーを使用します。 この拡張機能を使用して、レポート サーバーは、ODBC ドライバーが存在するすべてのデータベースのデータにアクセスできます。|  
  
 [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] データ処理 API を使用して、カスタム データ処理をレポート サーバーに追加できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のデータ プロバイダーに対するサポートが組み込まれています。 既に完全なデータ プロバイダーを実装している場合は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を実装する必要がありません。 ただし、セキュリティで保護された接続の資格情報やサーバー側の集計など、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005 に固有の機能を含むようにデータ プロバイダーの拡張を検討してください。  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] が備えている各データ処理拡張機能は、共通するインターフェイスのセットを使用します。 これにより、各拡張機能に比較機能が確実に実装されます。  
  
 独自のデータ ソース用のデータ処理拡張機能を開発できます。インターフェイスを使用して、データ処理の層を共通するデータベース インフラストラクチャに追加することもできます。 カスタム データ処理拡張機能を配置して、組織の既存レポート サーバーにデータをシームレスに統合できます。 ユーザーに提供するカスタム レポート スイートの一部として使用することもできます。  
  
 ![データ処理拡張機能のアーキテクチャ](../../../reporting-services/extensions/data-processing/media/bk-dataprocess-extensions.gif "データ処理拡張機能のアーキテクチャ")  
Reporting Services データ処理拡張機能のアーキテクチャ  
  
 カスタム [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を実装する利点は、次のとおりです。  
  
-   データ アクセス アーキテクチャを簡便化します。多くの場合、メンテナンスがしやすくなり、パフォーマンスが向上します。  
  
-   拡張機能固有の機能をユーザーに直接提示できます。  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 内のデータ ソースにユーザーが直接アクセスするための固有のインターフェイスです。  
  
## <a name="data-extension-process-flow"></a>データ拡張機能の処理フロー  
 カスタム データ拡張機能を開発する前に、レポート サーバーがデータ拡張機能を使用してどのようにデータを処理するか理解しておく必要があります。 レポート サーバーによって呼び出されるコンストラクターとメソッドも理解してください。  
  
 ![データ処理拡張機能のフローを処理](../../../reporting-services/extensions/data-processing/media/bk-ext-01.gif "プロセス フロー データ処理拡張機能")  
レポート サーバーによって呼び出されるデータ拡張機能のステップ バイ ステップ処理フロー  
  
 この図は、次の順序によるイベントを示しています。  
  
1.  レポート サーバーは、接続オブジェクトを作成し、レポートに関連付けられた接続文字列と資格情報を渡します。  
  
2.  レポートのコマンド テキストを使用して、コマンド オブジェクトを作成します。 このプロセスでは、コマンド テキストを解析し、コマンドのパラメーターを作成するコードがデータ処理拡張機能に含まれる場合もあります。  
  
3.  コマンド オブジェクトとパラメーターを処理した後、データ リーダーを生成します。データ リーダーによって、結果セットが返され、レポート サーバーがレポート データをレポート レイアウトに関連付けることができます。  
  
## <a name="developer-requirements"></a>開発者要件  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を開発するための要件は次のとおりです。  
  
-   レポート デザイナーまたはレポート サーバーがインストールされた配置用コンピューター  
  
-   開発用コンピューター[!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)]またはそれ以降、または[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]ソフトウェア開発キット (SDK) がインストールされています。  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の機能についてよく理解していること  
  
-   詳細に検討する[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vstecado](../../../includes/vstecado-md.md)]アーキテクチャ、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]データ プロバイダー、ADO.NET DataSet オブジェクト、および共通[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]インターフェイスです。  
  
-   開発エクスペリエンス、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]などの言語[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual c# または[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  