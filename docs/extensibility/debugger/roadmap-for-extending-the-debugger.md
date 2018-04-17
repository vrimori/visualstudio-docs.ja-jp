---
title: デバッガーを拡張するためのロードマップ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46c5a8a995644d6876457836674152eb3b3ccad7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="roadmap-for-extending-the-debugger"></a>デバッガーを拡張するためのロードマップ
このドキュメントを拡張するためのガイドとリファレンスの情報を提供、[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]とデバッガー、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ドキュメントをデバッグするには、サンプル、総合的なリファレンスと、デバッガーをカスタマイズする一般的な方法を示すいくつかの代表的なシナリオが含まれます。  
  
 コンパイラとその出力は、製品でのデバッグを実装するために実行する必要がありますを決定します。 場合、コンパイラ。  
  
-   Windows ネイティブ オペレーティング システムを対象とし、書き込みます、します。PDB ファイルに統合されているネイティブ コードのデバッグ エンジン (DE)、プログラムをデバッグすることができます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 DE または式エバリュエーターを実装する必要はありません。 C++ のプログラミング言語の構文については、式エバリュエーターが書き込まれます。  
  
-   Microsoft intermediate language (MSIL) を出力するプログラムをデバッグするには、マネージ コードのデバッグ エンジン DE にも統合されていると生成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 したがって、式エバリュエーターを実装する必要があるだけです。 サンプルの式エバリュエーターが提供されます。 詳細については、次のトピックを参照してください。  
  
     [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [評価式](../../extensibility/debugger/evaluating-expressions.md)  
  
     [式の評価のコンテキスト](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [中断モードでの式の評価](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [共通言語ランタイム式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   独自のオペレーティング システムや他の実行時環境のターゲット独自 DE を記述する必要があります。 ATL COM を使用して単純な DE を作成する方法についてのチュートリアルが提供されます。 詳細については、次のトピックを参照してください。  
  
     [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [チュートリアル: ATL COM を使用してデバッグ エンジンを構築します。](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [ポートのサプライヤーの実装](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)