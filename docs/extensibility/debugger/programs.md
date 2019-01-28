---
title: プログラム |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 372cf5c64fde2009b8bddf8fa5800788ba0d6501
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970189"
---
# <a name="programs"></a>Programs
デバッガーのアーキテクチャで、*プログラム*:  
  
-   スレッドのセットと、一連のモジュールの両方のコンテナーです。 Windows オペレーティング システムでは、プログラムの 1 つとの類似性はありません。  
  
     プログラムは、ある種のサブプロセスです。 たとえば、Web サイトをデバッグする場合、スクリプトをプログラムとして確認できます。 スクリプトのエンジン プロセスでスクリプトの実行中の他のスクリプトでは、独立したも、独自のスレッドのセット。 デバッグ エンジン (DE) は、プログラム、およびプロセスまたはスレッドにアタッチします。  
  
-   それ自体とで実行されているプロセスを識別できます。 プログラムから、デタッチ、および、存在する場合、それを作成した DE をについて説明しますにアタッチすることができます。 プログラムも実行、停止、続行でき終了します。  
  
-   そのすべてのスレッドを列挙できます。 プログラムでは、独自の逆アセンブリのストリームを指定することもし、特定のドキュメントの位置のすべてのコード コンテキストを列挙できます。  
  
-   によって表される、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスをプログラムがアタッチされている場合、前に、または実装によって、アタッチ プロセスの一部として作成します。 に従って、対応する各プログラムが作成されたポートは、プロセスのプログラムを列挙するときに[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)への引数として渡されたインターフェイス[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)します。 デバッグ エンジンを作成も`IDebugProgram2`に従ってプログラム ノードを表すプログラムでは、これらのプログラム インターフェイスは作成されません。 `IDebugProgramNode2` DE によって作成されたインターフェイスは、され、検出プロセスで実行中のプログラムにのみ使用ポートによって作成された、実際のデバッグでは、使用します。  
  
## <a name="see-also"></a>関連項目  
 [プロセス](../../extensibility/debugger/processes.md)   
 [プログラム ノード](../../extensibility/debugger/program-nodes.md)   
 [モジュール](../../extensibility/debugger/modules.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [ドキュメントの位置](../../extensibility/debugger/document-position.md)   
 [コード コンテキスト](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)