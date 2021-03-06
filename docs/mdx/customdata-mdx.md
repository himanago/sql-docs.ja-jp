---
title: CustomData (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 172915d99b231490cbdca24f70d1d38da27a1d3d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739307"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


  値を返します、 **CustomData**定義されている、それ以外の場合、接続文字列プロパティ**null**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>戻り値  
 **CustomData**関数を取得できます、 **CustomData**接続文字列プロパティと、構成など、多次元式 (MDX) 関数およびステートメントで使用する設定を渡す[UserName (MDX)](../mdx/username-mdx.md)と[CALL ステートメント (MDX)](../mdx/mdx-data-manipulation-call.md)です。 たとえば、この関数で指定できますを動的セキュリティ式内の文字列値の許可/拒否されたセット メンバーを選択する、 **CustomData**接続文字列プロパティです。  
  
## <a name="example"></a>例  
 次のクエリによって返される値を表示する、 **CustomData**計算されるメジャー内の関数。  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
