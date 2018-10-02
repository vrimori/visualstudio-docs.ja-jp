---
title: ノードのプログラム |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: caff608b85dc8fc563ace8f5d582dba1cba427c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545754"
---
# <a name="program-nodes"></a>プログラム ノード
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プログラム ノード](https://docs.microsoft.com/visualstudio/extensibility/debugger/program-nodes)します。  
  
デバッガーのアーキテクチャの観点から、**プログラム ノード**:  
  
-   プログラムの軽量の説明です。  
  
-   それ自体で実行されているからデタッチし、存在する場合、作成、デバッグ エンジン (DE) の説明に接続できますが、プロセスを識別できます。  
  
-   によって表される、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)インターフェイス、通常、DE またはポートを作成します。 プログラム ノードを呼び出すことによって、ポートに追加[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)します。 ポートに、[プログラム] ノードを追加するときに、このプログラムのノードが表すプログラムを格納しているプロセスに追加されます。  
  
 Debug パッケージの実装によって、デバッグ セッションを開始した後しばらくは、プログラムのノードが対応するプログラムを作成に使用されます。 プロセスは、そのプログラムの照会されたとき、プログラムが列挙されますが、プログラムの各ノードのいずれか。  
  
 プログラムにアタッチされて、前に、IDE には、プログラムの軽量の説明のみ必要があります。 この情報は、[プログラム] ノードから取得できます。 プログラムにアタッチされると、IDE をプログラムで実行されているすべてのスレッドの一覧などのより詳細な情報を表示する必要があります。 この情報は、プログラム自体から取得されます。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [プロセス](../../extensibility/debugger/processes.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

