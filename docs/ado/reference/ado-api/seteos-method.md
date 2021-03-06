---
title: SetEOS メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0db8c7972d6b647cdd021d43dbb3cdee1ba0452
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678530"
---
# <a name="seteos-method"></a>SetEOS メソッド
ストリームの末尾の位置を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>コメント  
 **SetEOS**の値を更新、 [EOS](../../../ado/reference/ado-api/eos-property.md)を現在のプロパティ[位置](../../../ado/reference/ado-api/position-property-ado.md)ストリームの末尾。 任意のバイトまたは現在の位置の文字は切り捨てられます。  
  
 [書き込み](../../../ado/reference/ado-api/write-method.md)、 [WriteText](../../../ado/reference/ado-api/writetext-method.md)、および[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)既存、余分な値は切り捨てられません**Stream**オブジェクトの場合、これらを切り捨てることができますバイト数または文字のストリームの終わりの新しい位置を設定して**SetEOS**します。  
  
> [!CAUTION]
>  設定した場合**EOS**ストリームの実際の終了前に、新しいすべてのデータは失われます**EOS**位置。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
