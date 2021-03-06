---
title: LinRegR2 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 42c703e703e8c557b4de8466a0cd1b686217fd4b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742061"
---
# <a name="linregr2-mdx"></a>LinRegR2 (MDX)


  セットの線形回帰を計算し、R、決定係数を返します<sup>2</sup>です。  
  
## <a name="syntax"></a>構文  
  
```  
  
LinRegR2(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression_y*  
 有効な数値式です。通常は、Y 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression_x*  
 有効な数値式です。通常は、X 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 最小ニ乗法による線型回帰では、回帰直線 (点の連続に最も適合する直線) の式を計算します。 回帰直線では次の式では、ここは傾き、b は切片は。  
  
 y = ax+b  
  
 **LinRegR2**関数は、指定した setagainst を評価します。 最初の数値式を示しますが、y 軸の値を取得します。 次に、2 番目の数値式が指定されている場合は、指定されているセットをその式に対して評価し、X 軸の値を取得します。 2 番目の数値した式が指定されていない場合、関数は、x 軸の値として指定されたセット内のセルの現在のコンテキストを使用します。 X-axisargument を指定していないは、時間ディメンションでよく使用されます。  
  
 、点のセットを取得した後に、 **LinRegR2**関数を示す統計的係数 R を返します<sup>2</sup>直線式が点にどの程度適合をについて説明します。  
  
> [!NOTE]  
>  **LinRegR2**関数は空のセルまたはテキストや論理値を含むセルを無視します。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="example"></a>例  
 次の例を示す統計的係数 R<sup>2</sup>の線形回帰式が売上数量メジャーと店舗売上メジャーの点の適合度をについて説明します。  
  
```  
LinRegR2(LastPeriods(10), [Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
