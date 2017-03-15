---
title: "プロセス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] をデバッグするには、処理します。"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# プロセス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッガーのアーキテクチャという点では **プロセス** :  
  
-   一連のプログラムのコンテナーです。  これは一連のスレッドのコンテナーの Windows プロセスに密接に似ています。  
  
-   自身IDまたは物理的な識別子を名前で指定できます。  
  
-   実行中のすべてのプログラムできます \(および\) スレッドを列挙します。  
  
-   実行しているものはポートおよびそれを含むマシンを記述できます。  
  
-   これで生成されるプログラムの一つ以上のプログラムを終了するために作成しプログラムを停止します。  
  
-   プロセスの起動時に作成された [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) のインターフェイスで表されます。  プロセスはデバッグ セッションの [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) マネージャー \(SDM\) を起動します。  
  
 デバッグのパッケージがプロセスに [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md) を呼び出してデバッグ \(DE\) エンジンをアタッチできます。  これは機能しますが処理できるプロセスで実行しているすべての可能なプログラムにアタッチすることを意味します。  たとえばde\-DE 共通言語ランタイムがプロセスにアタッチする場合マネージ コードを実行しているプログラムにアタッチします。  
  
## 参照  
 [Programs](../../extensibility/debugger/programs.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [パッケージをデバッグします。](../../extensibility/debugger/debug-package.md)   
 [エンジンをデバッグします。](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)