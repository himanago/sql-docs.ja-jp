---
title: CLR 統合アセンブリの管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9ae478cb2efc557acfd86e174d59a160fb8920c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686540"
---
# <a name="managing-clr-integration-assemblies"></a>CLR 統合アセンブリの管理
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  マネージド コードは、コンパイルされた後、アセンブリと呼ばれる単位で配置されます。 アセンブリは DLL ファイルまたは実行可能 (.exe) ファイルとしてパッケージ化されます。 実行可能ファイルが単独で実行できるのに対し、DLL は既存のアプリケーションでホストする必要があります。 マネージ DLL アセンブリに読み込まれ、によってホストされていることができます[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 アセンブリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のプロセスに読み込んで使用するには、CREATE ASSEMBLY ステートメントを使用してそのアセンブリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録する必要があります。 アセンブリは、ALTER ASSEMBLY ステートメントを使用してより最近のバージョンから更新することも、DROP ASSEMBLY ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から削除することも可能です。  
  
 アセンブリ情報が格納されている、 **sys.assembly_files**アセンブリがインストールされているデータベースのテーブル。 **Sys.assembly_files**テーブルには、次の列が含まれています。  
  
|[列]|説明|  
|------------|-----------------|  
|assembly_id|アセンブリに定義される ID。 この番号は、同じアセンブリに関連するすべてのオブジェクトに割り当てられます。|  
|NAME|オブジェクトの名前。|  
|file_id|最初のオブジェクトに関連付けられている各オブジェクトを識別する番号を指定した**assembly_id** 1 の値が指定されています。 複数のオブジェクトが関連付けられている場合**assembly_id**、以降の各し**file_id**値が 1 ずつインクリメントされます。|  
|content|アセンブリまたはファイルの 16 進数表記。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アセンブリの作成](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における SAFE、EXTERNAL_ACCESS、および UNSAFE CLR アセンブリの作成について説明します。  
  
 [アセンブリの変更](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における CLR アセンブリの更新について説明します。  
  
 [アセンブリの削除](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] からの CLR アセンブリの削除について説明します。  
  
## <a name="see-also"></a>参照  
 [CLR 統合のセキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [CLR 統合のコード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
