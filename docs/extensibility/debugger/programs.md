---
title: "プログラム |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03b4885e653d879e3aaec1d9a68bc9be144cb676
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="programs"></a>Programs
デバッガーのアーキテクチャの観点から、**プログラム**:  
  
-   スレッドのセットとモジュールのセットの両方のコンテナーです。 Windows オペレーティング システムでは、プログラムの 1 つとの類似性はありません。  
  
     プログラムは、一種のサブプロセスです。 たとえば、Web サイトをデバッグする際にスクリプトをプログラムとして表示できます。 スクリプトのスクリプト作成のエンジン プロセスの実行中に他のスクリプトの独立したさらに、独自のスレッドのセット。 デバッグ エンジン (DE) は、プログラム、していないプロセスまたはスレッドにアタッチします。  
  
-   それ自体で実行されているからデタッチして、存在する場合に、それを作成した DE の記述に関連付けることが、プロセスを識別できます。 プログラムは、実行、停止、続行、終了するとします。  
  
-   そのすべてのスレッドを列挙できます。 プログラムでは、独自の逆アセンブル ストリームも提供でき、特定のドキュメントの位置のすべてのコード コンテキストを列挙できます。  
  
-   によって表される、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス、プログラムをアタッチすると、前に、または実装によって、attach プロセスの一部として作成します。 に従って、対応する各プログラムが作成されたポートは、プロセスのプログラムを列挙するときに[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)への引数として渡されたインターフェイス[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)です。 またデバッグ エンジンを作成中に`IDebugProgram2`プログラム ノードに従ってプログラム、これらのプログラムを表すためのインターフェイスは作成されません。 `IDebugProgramNode2` DE によって作成されたインターフェイスは、ポートが作成されたもののみ使用されるプロセスで実行中のプログラムを検出中に、実際のデバッグでは、使用できます。  
  
## <a name="see-also"></a>参照  
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