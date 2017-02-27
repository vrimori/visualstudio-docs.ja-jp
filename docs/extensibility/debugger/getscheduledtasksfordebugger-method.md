---
title: "GetScheduledTasksForDebugger メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetScheduledTasksForDebugger メソッド、TaskScheduler クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetScheduledTasksForDebugger メソッド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

すべてのスケジュールされたタスクの配列を取得します。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこの内部のメンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## 戻り値  
 スケジュールされたすべてのタスクの配列。 各タスクが実行中または実行が完了しました。  
  
## 解説  
 このメソッドはスレッド セーフではありませんし、他のインスタンスと同時に使用しないで <xref:System.Threading.Tasks.TaskScheduler> 、デバッガーがその他のすべてのスレッドを中断された場合にのみ、デバッガーから呼び出すようにします。  
  
## 参照  
 [TaskScheduler クラス](../../extensibility/debugger/taskscheduler-class-internal-members.md)