---
title: プログラム |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3d1c1e72524c393fdb3adc4477ea9ae374fbfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="programs"></a>Programs
デバッガーのアーキテクチャの観点から、**プログラム**:  
  
-   スレッドのセットとモジュールのセットの両方のコンテナーです。 Windows オペレーティング システムでは、プログラムの 1 つとの類似性はありません。  
  
     プログラムは、一種のサブプロセスです。 たとえば、Web サイトをデバッグする際にスクリプトをプログラムとして表示できます。 スクリプトのスクリプト作成のエンジン プロセスの実行中に他のスクリプトの独立したさらに、独自のスレッドのセット。 デバッグ エンジン (DE) は、プログラム、していないプロセスまたはスレッドにアタッチします。  
  
-   それ自体で実行されているからデタッチして、存在する場合に、それを作成した DE の記述に関連付けることが、プロセスを識別できます。 プログラムは、実行、停止、続行、終了するとします。  
  
-   そのすべてのスレッドを列挙できます。 プログラムでは、独自の逆アセンブル ストリームも提供でき、特定のドキュメントの位置のすべてのコード コンテキストを列挙できます。  
  
-   によって表される、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス、プログラムをアタッチすると、前に、または実装によって、attach プロセスの一部として作成します。 に従って、対応する各プログラムが作成されたポートは、プロセスのプログラムを列挙するときに[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)への引数として渡されたインターフェイス[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)です。 またデバッグ エンジンを作成中に`IDebugProgram2`プログラム ノードに従ってプログラム、これらのプログラムを表すためのインターフェイスは作成されません。 `IDebugProgramNode2` DE によって作成されたインターフェイスは、ポートが作成されたもののみ使用されるプロセスで実行中のプログラムを検出中に、実際のデバッグでは、使用できます。  
  
## <a name="see-also"></a>関連項目  
 [プロセス](../../extensibility/debugger/processes.md)   
 [プログラムのノード](../../extensibility/debugger/program-nodes.md)   
 [モジュール](../../extensibility/debugger/modules.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [ドキュメントの位置](../../extensibility/debugger/document-position.md)   
 [コード コンテキスト](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)