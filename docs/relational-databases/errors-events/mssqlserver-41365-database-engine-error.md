---
title: MSSQLSERVER_41365 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 80b892c4627af5fd2db098c4e815f315d0bb85e1
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver41365"></a>MSSQLSERVER_41365
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41365|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|HK_MERGE_SCHEDULE_ERROR|  
|メッセージ テキスト|データベース %.*ls のトランザクション範囲 [%ld, %ld] に対するマージ要求がスケジュールされませんでした。 範囲を表すチェックポイント ファイルは、マージに使用できないか、実行中のマージの一部です。|  
  
## <a name="explanation"></a>説明  
範囲を表すチェックポイント ファイルは、マージに使用できないか、実行中のマージの一部です。  
  
## <a name="user-action"></a>ユーザーの操作  
同じ要求を再度発行する前に、マージ/待機にもっと適したトランザクション範囲を指定します。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
