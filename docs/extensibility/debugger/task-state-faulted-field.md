---
title: "TASK_STATE_FAULTED フィールド | Microsoft Docs"
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
  - "TASK_STATE_FAULTED フィールドに、タスク クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# TASK_STATE_FAULTED フィールド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

タスクはハンドルされない例外が発生したために終了しました。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## 解説  
 場合、 [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) フィールドには、この値が含まれています。、 <xref:System.Threading.Tasks.Task.Status%2A> プロパティを返します。 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>します。  
  
## 参照  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)