---
title: デバッガーを拡張するためのロードマップ |Microsoft Docs
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
ms.openlocfilehash: 7527d142b27e5b49bcf133429dc232614bad04a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942674"
---
# <a name="roadmap-for-extending-the-debugger"></a>デバッガーを拡張するためのロードマップ
このドキュメントは、拡張するためのガイドとリファレンスの情報を提供します。、[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]のデバッガー、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ドキュメントをデバッグするには、サンプル、総合的なリファレンスと、デバッガーをカスタマイズする一般的な方法を示すいくつかの代表的なシナリオが含まれます。  
  
 コンパイラとその出力は、お客様の製品にデバッグのセットアップに必要な内容を決定します。 場合、コンパイラ。  
  
- Windows ネイティブのオペレーティング システムを対象として、書き込み、*します。PDB*ファイルに統合されたネイティブ コード デバッグ エンジン (DE)、プログラムをデバッグできます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 DE または式エバリュエーターを実装する必要はありません。 C++ プログラミング言語の構文については、式エバリュエーターが書き込まれます。  
  
- Microsoft intermediate language (MSIL) が出力にも統合されているマネージ コードのデバッグ エンジン DE、プログラムをデバッグすることができますが生成されます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 したがって、式エバリュエーターのみを実装する必要があります。 サンプルの式エバリュエーターが提供されます。 詳細については、次のトピックを参照してください。  
  
   [式の評価](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
   [式を評価します。](../../extensibility/debugger/evaluating-expressions.md)  
  
   [式の評価コンテキスト](../../extensibility/debugger/expression-evaluation-context.md)  
  
   [中断モードでの式の評価](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
   [共通言語ランタイム式エバリュエーターを書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- 独自のオペレーティング システムや他のランタイム環境をターゲット、DE、独自に記述する必要があります。 ATL COM を使用して単純な DE を作成するチュートリアルが提供されます。 詳細については、次のトピックを参照してください。  
  
   [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
   [チュートリアル: ATL COM を使用してデバッグ エンジンを構築します。](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
   [ポート サプライヤーを実装します。](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
   [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>関連項目  
 [開始するには](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)