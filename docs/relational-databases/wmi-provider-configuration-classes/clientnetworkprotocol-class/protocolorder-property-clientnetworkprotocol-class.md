---
title: ProtocolOrder プロパティ (ClientNetworkProtocol クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolOrder Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5f0112546c356c8523392a63c4dcefa65769861a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669741"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>ProtocolOrder プロパティ (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  現在参照されているクライアントの注文番号で指定されたネットワーク プロトコルを取得、 [SetOrderValue メソッド (ClientNetworkProtocol クラス)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ClientNetworkProtocol クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md)によって使用されるネットワーク プロトコルを表すオブジェクトを[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 A **uint32**によって設定された現在参照されているクライアント ネットワーク プロトコルの順序番号を指定する値、 **OrderValue**メソッド。 クライアント ネットワーク プロトコルが無効の場合、この値は 0 になります。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルを構成します。](https://technet.microsoft.com/library/ms181035.aspx)   
 [クライアント ネットワーク プロトコルとネットワーク ライブラリの構成](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
