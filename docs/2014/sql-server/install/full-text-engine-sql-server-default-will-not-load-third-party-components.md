---
title: SQL Server 用 Microsoft Full-text Engine では既定で符号なしのサード パーティのコンポーネントが読み込まれません |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46632ec66e9ae17351cb10a65efbac9cedfb084a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125212"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>既定では Microsoft Full-Text Engine for SQL Server は署名のないサード パーティ コンポーネントを読み込まない
  既定では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] によって署名されていないコンポーネントを読み込みません。  
  
## <a name="component"></a>コンポーネント  
 フルテキスト検索  
  
## <a name="description"></a>説明  
 既定では、サーバー上に現在インストールされている PDF フィルターなどのサード パーティのフィルターは、アップグレード後に [!INCLUDE[msCoName](../../includes/msconame-md.md)] Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み込まれません。  
  
## <a name="corrective-action"></a>修正措置  
 サード パーティのフィルターを読み込むには、設定する必要があります*load_os_resource*オフにして*verify_signature*そのインスタンスにします。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
