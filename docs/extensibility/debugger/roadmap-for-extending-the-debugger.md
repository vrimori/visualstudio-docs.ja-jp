---
title: "デバッガーを拡張するためのロードマップ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
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
ms.openlocfilehash: 49df627aa42cd6cc6ac1430e4e68694fa51a2fc1
ms.lasthandoff: 02/22/2017

---
# <a name="roadmap-for-extending-the-debugger"></a>デバッガーを拡張するためのロードマップ
このドキュメントを拡張するためのガイドとリファレンスの情報を提供、[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]とデバッガー、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ドキュメントをデバッグするには、サンプル、包括的なリファレンス、およびデバッガーをカスタマイズする一般的な方法を示すいくつかの代表的なシナリオが含まれます。  
  
 コンパイラとその出力は、お使いの製品でのデバッグを実装するのに必要なものを決定します。 場合、コンパイラ。  
  
-   Windows ネイティブのオペレーティング システムを対象し、書き込みをします。PDB ファイルに統合されたネイティブ コードのデバッグ エンジン (DE) にプログラムをデバッグすることができます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 DE または式エバリュエーターを実装する必要はありません。 C++ プログラミング言語の構文については、式エバリュエーターが書き込まれます。  
  
-   Microsoft のプログラムをデバッグするには、マネージ コードのデバッグ エンジン DE にも統合されていると、中間言語 (MSIL) が出力を生成する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 したがって、式エバリュエーターを実装する必要があるだけです。 サンプルの式エバリュエーターが提供されます。 詳細については、次のトピックを参照してください。  
  
     [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [式を評価します。](../../extensibility/debugger/evaluating-expressions.md)  
  
     [式の評価コンテキスト](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [中断モードでの式の評価](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [共通言語ランタイムの式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   独自のオペレーティング システムやその他の実行時環境のターゲット独自 DE を記述する必要があります。 ATL COM を使用して単純な DE を作成する方法についてのチュートリアルが提供されます。 詳細については、次のトピックを参照してください。  
  
     [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [チュートリアル: ATL COM を使用してデバッグ エンジンを構築します。](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [ポートのサプライヤーを実装します。](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
