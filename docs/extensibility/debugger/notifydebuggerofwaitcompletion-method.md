---
title: "NotifyDebuggerOfWaitCompletion メソッド | Microsoft Docs"
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
  - "NotifyDebuggerOfWaitCompletion メソッド、タスク クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# NotifyDebuggerOfWaitCompletion メソッド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プレース ホルダー メソッドは、デバッガーのブレークポイント ターゲットとして使用します。 このメソッドは、インライン関数、または最適化されたさせないでください。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
## 構文  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## 解説  
 タスクを持つすべての結合操作は、デバッガー通知ビットが設定されている場合、このメソッドを呼び出す必要があります。  
  
## 必要条件  
  
## 参照  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)