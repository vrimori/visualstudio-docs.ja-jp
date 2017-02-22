---
title: "TaskScheduler クラスの内部メンバー | Microsoft Docs"
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
  - "TaskScheduler クラス [.NET Framework のデバッグ エンジン]"
  - "デバッグ エンジンは、TaskScheduler クラス [.NET Framework]"
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# TaskScheduler クラスの内部メンバー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このトピックの内部メンバーの説明、 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 役立つクラスは、カスタムのデバッガーを実装します。 このクラスの概要については、次を参照してください。、 <xref:System.Threading.Tasks.TaskScheduler> リファレンス トピックです。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
 .NET Framework からこれらの内部メンバーにアクセスできないため、次の構文は共通中間言語 \(CIL\) に提供されます。  
  
## 構文  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## メンバー  
  
### メソッド  
  
|名前|説明|  
|--------|--------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|すべてのスケジュールされたタスクの配列を取得します。|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|すべての配列を取得 <xref:System.Threading.Tasks.TaskScheduler> 現在アクティブなオブジェクトです。|  
  
## 解説  
  
## 参照  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [.NET Framework の並列拡張機能の内部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)