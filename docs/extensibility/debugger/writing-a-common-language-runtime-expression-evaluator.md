---
title: "共通言語ランタイムの式エバリュエーターを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d52a9dbed6cec64426247a0b92bff2b8ec98ec97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>共通言語ランタイムの式エバリュエーターの書き込み
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 式エバリュエーター (EE) は、構文を処理するデバッグ エンジン (DE) の一部とデバッグ中のコードを生成するプログラミング言語のセマンティクスです。 式は、プログラミング言語のコンテキスト内で評価される必要があります。 たとえば、一部の言語で式"A B"、"A の合計と B" 他の言語では、同じ式が「A または b.」を可能性があります。 したがって、個別の EE 書き込む必要があります、Visual Studio IDE でデバッグ対象のオブジェクト コードを生成するプログラミング言語ごとにします。  
  
 Visual Studio デバッグ パッケージの一部の機能は、プログラミング言語のコンテキストでコードを解釈する必要があります。 他の式に入力したユーザーをブレークポイントで実行を停止したときなど、**ウォッチ**ウィンドウを評価して表示する必要があります。 式を入力して、ユーザーがローカル変数の値を変更するも、**ウォッチ**ウィンドウに、または、**イミディ エイト**ウィンドウです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [共通言語ランタイムおよび式の評価](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Visual Studio IDE に独自のプログラミング言語を統合するときに、EE を記述独自の言語のコンテキスト内で式を評価することでは、Microsoft intermediate language (MSIL) にコンパイルするについて説明します。デバッグ エンジンを書き込まずにします。  
  
 [式エバリュエーターのアーキテクチャ](../../extensibility/debugger/expression-evaluator-architecture.md)  
 EE の必要なインターフェイスを実装し、共通言語ランタイムのシンボル プロバイダー (SP) およびバインダー インターフェイスを呼び出す方法について説明します。  
  
 [式エバリュエーターの登録](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 ノート EE 必要があります、共通言語ランタイムと Visual Studio のランタイム環境でクラス ファクトリとしてそれ自体に登録されています。  
  
 [式エバリュエーターの実装](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 式を評価するプロセスがデバッグ エンジン (DE)、シンボル プロバイダー (SP)、バインダー オブジェクト、および、式エバリュエーター (EE) に含まれますについて説明します。  
  
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)  
 方法については、実行が一時停止、ときにデバッグ パッケージを呼び出すローカル変数と引数の一覧を取得する DE について説明します。  
  
 [[ウォッチ] ウィンドウの式の評価](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Visual Studio デバッグ パッケージがそのウォッチ式のリスト内の各式の現在の値を決定する DE を呼び出す方法について説明します。  
  
 [ローカルの値の変更](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 ローカルの値を変更するには、[ローカル] ウィンドウの各行が名、型、およびローカルの現在の値を提供する関連付けられているオブジェクトについて説明します。  
  
 [型のビジュアライザーおよびカスタム ビューアーの実装](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 ビジュアライザーの型とカスタム ビューアーをサポートするコンポーネントによって実装される必要があるどのインターフェイスについて説明します。  
  
## <a name="see-also"></a>参照  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)