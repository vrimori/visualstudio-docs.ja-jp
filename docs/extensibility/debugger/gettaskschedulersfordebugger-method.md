---
title: "GetTaskSchedulersForDebugger メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTaskSchedulersForDebugger メソッド、TaskScheduler クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetTaskSchedulersForDebugger メソッド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

すべての配列を取得 <xref:System.Threading.Tasks.TaskScheduler> 現在アクティブなオブジェクトです。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## 戻り値  
 すべての配列 <xref:System.Threading.Tasks.TaskScheduler> これで現在アクティブなオブジェクト <xref:System.AppDomain>します。  
  
## 解説  
 このメソッドはスレッド セーフではありませんし、他のインスタンスと同時に使用しないで <xref:System.Threading.Tasks.TaskScheduler>します。 デバッガーがその他のすべてのスレッドを中断された場合にのみ、デバッガーから呼び出すことはできます。  
  
## 参照  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)