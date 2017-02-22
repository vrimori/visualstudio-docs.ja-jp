---
title: "TASK_STATE_RAN_TO_COMPLETION フィールド | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TASK_STATE_RAN_TO_COMPLETION フィールドに、タスク クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# TASK_STATE_RAN_TO_COMPLETION フィールド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

タスクの実行は正常に完了しました。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## 解説  
 場合、 [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) フィールドには、この値が含まれています。、 <xref:System.Threading.Tasks.Task.Status%2A> プロパティを返します。 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>します。  
  
## 参照  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)