---
title: デバッガーを拡張するためのロードマップ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fce5c11b5393bb8e3887b1369866a5f0906195d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242106"
---
# <a name="roadmap-for-extending-the-debugger"></a>デバッガーを拡張するためのロードマップ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このドキュメントは、拡張するためのガイドとリファレンスの情報を提供します。、[!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)]のデバッガー、[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ドキュメントをデバッグするには、サンプル、総合的なリファレンスと、デバッガーをカスタマイズする一般的な方法を示すいくつかの代表的なシナリオが含まれます。  
  
 コンパイラとその出力は、お使いの製品でのデバッグを実装するために必要事項を決定します。 場合、コンパイラ。  
  
-   Windows ネイティブのオペレーティング システムを対象として、書き込み、します。PDB ファイルに統合されたネイティブ コード デバッグ エンジン (DE)、プログラムをデバッグできます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 DE または式エバリュエーターを実装する必要はありません。 C++ プログラミング言語の構文については、式エバリュエーターが書き込まれます。  
  
-   Microsoft intermediate language (MSIL) が出力にも統合されているマネージ コードのデバッグ エンジン DE、プログラムをデバッグすることができますが生成されます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 したがって、式エバリュエーターのみを実装する必要があります。 サンプルの式エバリュエーターが提供されます。 詳細については、次のトピックを参照してください。  
  
     [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [評価式](../../extensibility/debugger/evaluating-expressions.md)  
  
     [式の評価のコンテキスト](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [中断モードでの式の評価](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [共通言語ランタイム式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   独自のオペレーティング システムや他のランタイム環境をターゲット、DE、独自に記述する必要があります。 ATL COM を使用して単純な DE を作成するチュートリアルが提供されます。 詳細については、次のトピックを参照してください。  
  
     [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [チュートリアル: ATL COM を使用してデバッグ エンジンを構築します。](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [ポートのサプライヤーの実装](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

