---
title: "プログラムのノード | Microsoft Docs"
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
  - "プログラムのノード、デバッグ コンテキスト"
  - "[デバッグ SDK] プログラムのノードのデバッグ"
  - "プログラムのノードを追加"
  - "置き換え、プログラムのノード"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# プログラムのノード
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッガーのアーキテクチャという点では **プログラムのノード** :  
  
-   プログラムの軽量について説明します。  
  
-   実行しているプロセス自身を特定して記述するには作成したデバッグ エンジンをアタッチし\(DE\) からデタッチできます \(存在する場合\)。  
  
-   通常de\-DE またはポートによって作成された [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) のインターフェイスにより表されます。  プログラムのノードはポートに [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) を呼び出して追加されます。  プログラムのノードはポートに追加するとこのプログラムのノードが表すするプログラムを含むプロセスに追加されます。  
  
 あるデバッグ セッションがデバッグのパッケージの実装によってプログラムのノード呼び出された後に対応するプログラムを作成するために使用されます。  プロセスがプログラムに対する問い合わせを受けるとプログラムの各ノードのプログラムは1 つ列挙されます。  
  
 プログラムがアタッチされる前プログラムの軽量の説明だけです。  この情報はプログラムのノードから取得できます。  プログラムは一度にIDE で実行するすべてプログラムのスレッド一覧などの詳細情報を表示する必要があるアタッチされます。  この情報はプログラム自体から派生します。  
  
## 参照  
 [Programs](../../extensibility/debugger/programs.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [エンジンをデバッグします。](../../extensibility/debugger/debug-engine.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)