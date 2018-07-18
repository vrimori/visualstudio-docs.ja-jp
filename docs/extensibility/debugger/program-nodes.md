---
title: ノードをプログラム |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50ab93c31a340bf8a2f4e2deb5f202707d7826b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099604"
---
# <a name="program-nodes"></a>プログラムのノード
デバッガーのアーキテクチャの観点から、**プログラム ノード**:  
  
-   プログラムの軽量の説明です。  
  
-   それ自体で実行されているからデタッチして、存在する場合、作成、デバッグ エンジン (DE) の説明に関連付けることが、プロセスを識別できます。  
  
-   によって表される、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)インターフェイス、通常、DE またはポートを作成します。 プログラムのノードを呼び出すことによって、ポートに追加[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)です。 ポートに、[プログラム] ノードを追加するときに、このプログラムのノードが表すプログラムを含むプロセスに追加されます。  
  
 デバッグ パッケージの実装によって、デバッグ セッションの開始後にいずれかの時点は、プログラムのノードが対応するプログラムを作成に使用されます。 そのプログラムをプロセスが照会されたとき、プログラムが列挙されますが、プログラムの各ノードのいずれか。  
  
 プログラムにアタッチされて、前に、IDE には、プログラムの軽量の説明のみ必要があります。 この情報は、[プログラム] ノードから取得できます。 プログラムに結び付けられる、IDE をプログラムで実行されているすべてのスレッドのリストなどのより詳細な情報を表示する必要があります。 この情報は、プログラム自体から取得されます。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)