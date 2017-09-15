---
title: "メンテナンス プランの作成 | Microsoft Docs"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maintenance plans [SQL Server], creating
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: adab1fc3a3a009a4a6fe74ddbe9ee97f8c128bdf
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-maintenance-plan"></a>メンテナンス プランの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、単一サーバーまたはマルチサーバーのメンテナンス プランを作成する方法について説明します。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でメンテナンス プランを作成する方法には、メンテナンス プラン ウィザードを使用する方法とデザイン画面を使用する方法の 2 とおりがあります。 基本的なメンテナンス プランを作成する場合は、ウィザードが最適です。それに対して、デザイン画面を使用してプランを作成すると、高度なワークフローを利用できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
     
     [前提条件](#Prerequisite)  
  
     [Security](#Security)  
  
-   **メンテナンス プランを作成するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 マルチサーバー メンテナンス プランを作成するには、1 台のマスター サーバーと 1 台以上の対象サーバーを含むマルチサーバー環境を構成する必要があります。 マルチサーバー メンテナンス プランは、マスター サーバー上で作成および管理する必要があります。 このプランは対象サーバー上でも表示できますが、対象サーバーでは管理できません。 
 
###  <a name="Prerequisite"></a> 前提条件  
[Agent XP サーバー構成オプション](../../database-engine/configure-windows/agent-xps-server-configuration-option.md) を有効にする必要があります。
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> アクセス許可  
 メンテナンス プランを作成または管理するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-a-maintenance-plan-using-the-maintenance-plan-wizard"></a>メンテナンス プラン ウィザードを使用してメンテナンス プランを作成するには  
  
1.  オブジェクト エクスプローラーで、プラス記号をクリックして、メンテナンス プランを作成するサーバーを展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  **[メンテナンス プラン]** フォルダーを右クリックし、 **[メンテナンス プラン ウィザード]**をクリックします。  
  
4.  ウィザードの手順に従って、メンテナンス プランを作成します。 詳細については、「 [Use the Maintenance Plan Wizard](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)」をご覧ください。  
  
#### <a name="to-create-a-maintenance-plan-using-the-design-surface"></a>デザイン画面を使用してメンテナンス プランを作成するには  
  
1.  オブジェクト エクスプローラーで、プラス記号をクリックして、メンテナンス プランを作成するサーバーを展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  **[メンテナンス プラン]** フォルダーを右クリックし、**[新しいメンテナンス プラン]** をクリックします。  
  
4.  「[メンテナンス プランの作成 &#40;メンテナンス プラン デザイン画面&#41;](../../relational-databases/maintenance-plans/create-a-maintenance-plan-maintenance-plan-design-surface.md)」の手順に従って、メンテナンス プランを作成します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-maintenance-plan"></a>メンテナンス プランを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE msdb;  
    GO  
    --  Adds a new job, executed by the SQL Server Agent service, called "HistoryCleanupTask_1".  
    EXEC dbo.sp_add_job  
       @job_name = N'HistoryCleanupTask_1',   
       @enabled = 1,   
       @description = N'Clean up old task history' ;   
    GO  
    -- Adds a job step for reorganizing all of the indexes in the HumanResources.Employee table to the HistoryCleanupTask_1 job.   
    EXEC dbo.sp_add_jobstep  
        @job_name = N'HistoryCleanupTask_1',   
        @step_name = N'Reorganize all indexes on HumanResources.Employee table',   
        @subsystem = N'TSQL',   
        @command = N'USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_LoginID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_rowguid ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX PK_Employee_BusinessEntityID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    ',   
        @retry_attempts = 5,   
        @retry_interval = 5 ;   
    GO  
    -- Creates a schedule named RunOnce that executes every day when the time on the server is 23:00.   
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',   
        @freq_type = 4,   
        @freq_interval = 1,   
        @active_start_time = 233000 ;   
    GO  
    -- Attaches the RunOnce schedule to the job HistoryCleanupTask_1.   
    EXEC sp_attach_schedule  
       @job_name = N'HistoryCleanupTask_1'  
       @schedule_name = N'RunOnce' ;   
    GO  
  
    ```  
  
 詳細については、以下をご覧ください。  
  
-   [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)  
  
-   [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
-   [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
-   [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
