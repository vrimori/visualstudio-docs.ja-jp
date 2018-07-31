---
title: ノードのプログラム |Microsoft Docs
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
ms.openlocfilehash: 27007773cfe8d8a8b595ee9b1921f35376bf2231
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251063"
---
# <a name="program-nodes"></a>プログラム ノード
デバッガーのアーキテクチャで、*プログラム ノード*:  
  
-   プログラムの軽量の説明です。  
  
-   それ自体とで実行されているプロセスを識別できます。 プログラム ノードから、デタッチ、および、存在する場合は、作成、デバッグ エンジン (DE) を記述にアタッチすることができます。  
  
-   によって表される、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)インターフェイス、通常、DE またはポートを作成します。 プログラム ノードを呼び出すことによって、ポートに追加[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)します。 ポートに、[プログラム] ノードを追加するときに、このプログラムのノードが表すプログラムを格納しているプロセスに追加されます。  
  
 Debug パッケージの実装によって、デバッグ セッションを開始した後しばらくは、プログラムのノードが対応するプログラムを作成に使用されます。 プロセスは、そのプログラムの照会されたとき、プログラムが列挙されますが、プログラムの各ノードのいずれか。  
  
 プログラムにアタッチされて、前に、IDE には、プログラムの軽量の説明のみ必要があります。 この情報は、[プログラム] ノードから取得できます。 プログラムにアタッチされると、プログラムで実行されているすべてのスレッドの一覧などのより詳細な情報が表示されます。 この情報は、プログラム自体から取得されます。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)