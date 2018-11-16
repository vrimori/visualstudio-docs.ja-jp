---
title: 共通言語ランタイム式エバリュエーターの書き込み |Microsoft Docs
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
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfd368bb0302fec1fcf9fdd1f6e6e069377846ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783013"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>共通言語ランタイム式エバリュエーターの書き込み
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター (EE) は、構文を処理するデバッグ エンジン (DE) の一部と、デバッグ中のコードを生成したプログラミング言語のセマンティクスです。 プログラミング言語のコンテキスト内で式を評価する必要があります。 たとえば、一部の言語で式の"A + B"、"A の合計と B の" 他の言語で同じ式は「A または b.」可能性があります。 そのため、個別の EE 書き込む必要がある各プログラミング言語、Visual Studio IDE でデバッグ対象のオブジェクト コードを生成します。  
  
 Visual Studio のデバッグ パッケージの一部の側面は、プログラミング言語のコンテキストでコードを解釈する必要があります。 他の式に入力したユーザーをブレークポイントで実行を停止したときなど、**ウォッチ**ウィンドウを評価および表示する必要があります。 式を入力して、ユーザーがローカル変数の値を変更するも、**ウォッチ**ウィンドウに、**イミディ エイト**ウィンドウ。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [共通言語ランタイムおよび式の評価](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 独自のプログラミング言語を Visual Studio IDE に統合するときに、EE を記述独自の言語のコンテキスト内で式を評価するのに対応できることを Microsoft intermediate language (MSIL) にコンパイルするについて説明します。デバッグ エンジンを書かずにします。  
  
 [式エバリュエーターのアーキテクチャ](../../extensibility/debugger/expression-evaluator-architecture.md)  
 EE の必要なインターフェイスを実装し、共通言語ランタイムのシンボル プロバイダー (SP) とバインダー インターフェイスを呼び出す方法について説明します。  
  
 [式エバリュエーターの登録](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 ノート EE する必要があります、共通言語ランタイムと Visual Studio のランタイム環境でクラス ファクトリとして自体に登録します。  
  
 [式エバリュエーターの実装](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 式の評価プロセスを含むデバッグ エンジン (DE)、シンボル プロバイダー (SP)、バインダー オブジェクト、式エバリュエーター (EE) および方法について説明します。  
  
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)  
 方法については、実行が一時停止したときに、デバッグ パッケージを呼び出すローカル変数と引数の一覧を取得する DE について説明します。  
  
 [[ウォッチ] ウィンドウの式の評価](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Visual Studio のデバッグ パッケージがそのウォッチ リスト内の各式の現在の値を決定する DE を呼び出す方法について説明します。  
  
 [ローカルの値の変更](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 ローカルの値を変更するには、[ローカル] ウィンドウの各行が、名前、種類、およびローカルの現在の値を提供する関連付けられているオブジェクトについて説明します。  
  
 [型のビジュアライザーおよびカスタム ビューアーの実装](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 型のビジュアライザーおよびカスタム ビューアーをサポートするためにコンポーネントによって実装される必要があるインターフェイスについて説明します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

