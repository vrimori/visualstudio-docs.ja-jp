---
title: "例外のトラブルシューティング : System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "PersistenceException 例外"
  - "System.Workflow.Runtime.Hosting.PersistenceException 例外"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Workflow.Runtime.Hosting.PersistenceException
<xref:System.Workflow.Runtime.Hosting.PersistenceException> 例外は、永続性サービスが要求を実行できない場合にスローされます。  
  
## コメント  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> は、完了したスコープまたはワークフロー インスタンスの状態をデータベースにコミットする要求を完了できない場合に <xref:System.Workflow.Runtime.Hosting.PersistenceException> をスローします。  
  
 <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> クラスまたは <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> クラスから派生させることにより永続性サービスを実装する場合、適切なメッセージを指定して <xref:System.Workflow.Runtime.Hosting.PersistenceException> をスローし、ワークフロー ランタイム エンジンからの要求を実行できなくするサービスによって発生したエラー状況を示すことができます。  
  
 詳細については、「<xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>」を参照してください。  
  
## 参照  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)