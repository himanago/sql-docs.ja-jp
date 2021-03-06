---
title: 子パッケージの実装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- child packages
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f415816f935e03b6b533fded2fb00760a101526d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100186"
---
# <a name="implementation-of-child-packages"></a>子パッケージの実装
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を使用して負荷分散を実装すると、子パッケージが他のサーバーにインストールされ、利用可能な CPU 時間またはサーバー時間を活用することができます。 子パッケージを作成および実行するには、次の手順を実行します。  
  
-   子パッケージをデザインします。  
  
-   パッケージをリモート サーバーに移動します。  
  
-   子パッケージを実行するステップを含む SQL Server エージェント ジョブをリモート サーバー上に作成します。  
  
-   SQL Server エージェント ジョブと子パッケージをテストおよびデバッグします。  
  
 子パッケージをデザインする際、子パッケージにはデザイン上の制限がないため、目的の機能をすべて追加できます。 ただし、パッケージからデータにアクセスする場合は、パッケージを実行するサーバーからそのデータにアクセスできなければなりません。  
  
 子パッケージを実行する親パッケージを識別するには、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のソリューション エクスプローラーでパッケージを右クリックし、**[エントリ ポイント パッケージ]** をクリックします。  
  
 子パッケージをデザインしたら、次に、そのパッケージをリモート サーバーに配置します。  
  
## <a name="moving-the-child-package-to-the-remote-instance"></a>リモート インスタンスへの子パッケージの移動  
 パッケージを他のサーバーに移動する方法は何種類かあります。 次の 2 つの方法をお勧めします。  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用してパッケージをエクスポートします。  
  
-   パッケージを配置します。パッケージを配置するには、配置するパッケージを含むプロジェクトの配置ユーティリティをビルドした後、パッケージ インストール ウィザードを実行し、パッケージをファイル システムまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスにインストールします。 詳細については、次を参照してください。[パッケージの配置&#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)します。  
  
 この配置は、使用する各リモート サーバーに対してそれぞれ行う必要があります。  
  
## <a name="creating-the-sql-server-agent-jobs"></a>SQL Server エージェント ジョブの作成  
 子パッケージをさまざまなサーバーに配置した後、子パッケージを格納した各サーバー上に SQL Server エージェント ジョブを作成します。 SQL Server エージェント ジョブには、ジョブ エージェントの呼び出し時に子パッケージを実行するステップが含まれています。 SQL Server エージェント ジョブは定期ジョブではありません。つまり、子パッケージは、親パッケージによって呼び出されたときだけ実行されます。 ジョブの成功や失敗に関する親パッケージへの通知は、SQL Server エージェント ジョブの成功や失敗、およびそのジョブが正常に呼び出されたかどうかを表すものであり、子パッケージが実行されたかどうかや、その成功や失敗については反映されません。  
  
## <a name="debugging-the-sql-server-agent-jobs-and-child-packages"></a>SQL Server エージェント ジョブと子パッケージのデバッグ  
 次のいずれかの方法を使用して、SQL Server エージェント ジョブとその子パッケージをテストできます。  
  
-   **[デバッグ]** メニューの  / **[デバッグなしで開始]** をクリックして、SSIS デザイナーで各子パッケージを実行します。  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用してリモート コンピューター上の個別の SQL Server エージェント ジョブを実行し、パッケージが実行されていることを確認します。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントのジョブから実行するパッケージのトラブルシューティング方法については、[!INCLUDE[msCoName](../includes/msconame-md.md)] サポート技術情報の「[SQL Server エージェントのジョブ ステップから SSIS パッケージを呼び出したときに SSIS パッケージが実行されない](http://support.microsoft.com/kb/918760)」を参照してください。  
  
 SQL Server エージェントは、ジョブ ステップを実行するたびに、プロキシに対してサブシステムのアクセス許可を確認し、プロキシへのアクセスを確立します。  
  
 プロキシは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] で作成できます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   ブログ エントリ「 [SSIS: 親パッケージ変数にアクセスする](http://go.microsoft.com/fwlink/?LinkId=257729)、consultingblogs.emc.com します。  
  
-   ブログ エントリ「 [SSIS: 子パッケージのインプロセスまたはアウト プロセスを実行する必要がありますか?](http://go.microsoft.com/fwlink/?LinkId=220819)、consultingblogs.emc.com。  
  
  
