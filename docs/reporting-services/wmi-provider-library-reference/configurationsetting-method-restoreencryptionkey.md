---
title: RestoreEncryptionKey メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6d19ecb9c4f14c0f9750a7344a6c2c442785cbb0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52416139"
---
# <a name="configurationsetting-method---restoreencryptionkey"></a>ConfigurationSetting メソッド - RestoreEncryptionKey
  指定した暗号化キーをレポート サーバー データベースに再適用します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>パラメーター  
 *KeyFile[]*  
 [out] 暗号化された暗号化キーを含む配列。  
  
 *[データ型]*  
 [out] メソッドによって返される配列の長さ。  
  
 *パスワード*  
 暗号化キーの暗号化に使用される文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
 *ExtendedErrors[]*  
 [out] 呼び出しによって返されたその他のエラーを含む文字列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
 レポート サーバー データベースのレポート サーバーに既にエントリが存在する場合、そのエントリは削除されます。 その後、指定した暗号化キーとレポート サーバーの公開キーを使用して、新しいエントリが作成されます。  
  
 このメソッドが最も効果的なのは、暗号化キーの一覧を消去する [DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-deleteencryptionkey.md) メソッドの後に呼び出した場合です。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
