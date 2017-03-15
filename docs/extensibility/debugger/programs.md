---
title: "プログラム |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 982d966208433905115e76a36d358c656005e3d3
ms.lasthandoff: 02/22/2017

---
# <a name="programs"></a>Programs
デバッガーのアーキテクチャの観点から、**プログラム**:  
  
-   スレッドのセットと一連のモジュールの両方のコンテナーです。 Windows オペレーティング システムでは、プログラムの&1; つの例はありません。  
  
     プログラムは、サブプロセスの一種です。 たとえば、Web サイトをデバッグするとき、スクリプトは、プログラムとして表示できます。 スクリプトのスクリプト作成のエンジン プロセスの実行中に他のスクリプトに依存しないも、独自のスレッドのセットです。 デバッグ エンジン (DE) は、プロセスやスレッドを行わないと、プログラムにアタッチします。  
  
-   それ自体で実行されからデタッチして、存在する場合は、作成した DE の説明に関連付けることが、プロセスを識別できます。 プログラムは、実行、停止、続行、終了するとします。  
  
-   すべてのスレッドを列挙できます。 プログラムでは、独自の逆アセンブル ストリームを提供することもし、指定されたドキュメントの位置のすべてのコードのコンテキストを列挙できます。  
  
-   によって表される、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス、プログラムを追加すると、前に、または実装によって、アタッチ プロセスの一部として作成します。 に従って、対応する各プログラムが作成されたポートは、プロセスのプログラムを列挙するときに[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)への引数として渡されたインターフェイス[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)します。 デバッグ エンジンを作成も`IDebugProgram2`プログラム ノードに従って、これらのプログラムのプログラムを表すためのインターフェイスは作成されません。 `IDebugProgramNode2`デによって作成されたインターフェイスは、ポートが作成されたものは、プロセスで実行中のプログラムを検出するためにのみ使用されますが、実際のデバッグに使用します。  
  
## <a name="see-also"></a>関連項目  
 [プロセス](../../extensibility/debugger/processes.md)   
 [プログラムのノード](../../extensibility/debugger/program-nodes.md)   
 [モジュール](../../extensibility/debugger/modules.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [エンジンをデバッグします。](../../extensibility/debugger/debug-engine.md)   
 [ドキュメントの位置](../../extensibility/debugger/document-position.md)   
 [コードのコンテキスト](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
