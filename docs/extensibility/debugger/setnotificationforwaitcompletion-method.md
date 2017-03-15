---
title: "SetNotificationForWaitCompletion メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SetNotificationForWaitCompletion メソッド、タスク クラス [.NET Framework のデバッグ エンジン]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# SetNotificationForWaitCompletion メソッド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定または TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION 状態ビットをクリアします。  
  
 **名前空間:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **アセンブリ:** \(mscorlib.dll\) の mscorlib  
  
## 構文  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### パラメーター  
 `enabled`  
  
 `true` ビットを設定するには `false` 未設定の状態ビットです。  
  
## 例外  
  
## 解説  
 デバッガーは、async メソッド本体の外部のステップに役立つこのビットを設定します。 場合 `enabled` は `true`, 、このメソッドは、まだ完了されていないタスクでのみ呼び出す必要があります。 場合 `enabled` は `false`, 、完了したタスクにこのメソッドを呼び出すことができます。 いずれの場合にのみ使用してください promise スタイル タスクの。  
  
## 必要条件  
  
## 参照  
 [Task クラス](../../extensibility/debugger/task-class-internal-members.md)