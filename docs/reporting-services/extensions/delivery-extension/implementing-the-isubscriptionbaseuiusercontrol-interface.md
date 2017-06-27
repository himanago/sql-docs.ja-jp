---
title: "ISubscriptionBaseUIUserControl インターフェイスを実装する |Microsoft ドキュメント"
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
- user controls [Reporting Services]
- ISubscriptionBaseUIUserControl interface
- delivery extensions [Reporting Services], user controls
ms.assetid: a1e9122c-aa0b-45de-b536-4f1202875ab1
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 5b509345723b137941c2f00c054c77f076035dc2
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="implementing-the-isubscriptionbaseuiusercontrol-interface"></a>ISubscriptionBaseUIUserControl インターフェイスの実装
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信拡張機能には、レポート マネージャーで拡張機能固有の情報を収集するためのサブスクリプション ユーザー インターフェイス (UI) の実装を含めることができます。 ユーザーが新しいサブスクリプションを作成するか既存のサブスクリプションを変更するとき、UI が呼び出されます。 新しいサブスクリプションの作成時には、UI に適切な既定値が表示され、ユーザーは配信プロバイダーと対話できます。 サブスクリプションの変更時には、現在のサブスクリプションの情報が UI にあらかじめ表示されます。  
  
 配信拡張機能では、サブスクリプション UI が ASP.NET ユーザー コントロールとして提供されます。 レポート サーバーでは、サブスクリプション UI を表示するとき、配信拡張機能で定義されたユーザー コントロールを組み込みます。 この機能を可能にする抽象メソッドを提供する基本インターフェイスは <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスです。 このインターフェイスでは、入力値の検証など、一般的な操作が正しく実行されます。 また、基本ユーザー コントロールには、レポート サーバーがサブスクリプション間での一貫性を保つために使用する既定のプロパティ セットが用意されています。 これらのプロパティは、レポート マネージャーと統合された配信拡張機能で必要となります。  
  
 レポート マネージャー用のサブスクリプション UI を作成するため、配信プロバイダーに <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装できます。 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスは、ユーザーがサブスクリプション設定の値を入力できるようにし、配信拡張機能に必要な設定を処理し、設定を検証するためのインフラストラクチャを提供します。  
  
> [!NOTE]  
>  配信拡張機能の一部として <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスを実装する必要はありません。 配信拡張機能を使用するサブスクリプションは、SOAP API メソッドの <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> および <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> を代用していつでも作成できます。 サブスクリプションおよび配信を管理するための SOAP API 機能の詳細については、次を参照してください。 [Subscription and Delivery Methods](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md)です。  
  
 <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイスは <xref:Microsoft.ReportingServices.Interfaces.IExtension> を拡張します。 ユーザー コントロールを実装する<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>から継承する必要がありますも**System.Web.UI.WebControls.WebControl**です。 詳細については、 **WebControl**クラスを参照してください、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]開発者ガイド 』。  
  
 使用する方法の例については、<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>インターフェイスを参照してください[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="see-also"></a>参照  
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  