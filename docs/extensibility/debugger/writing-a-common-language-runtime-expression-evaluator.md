---
title: "共通言語ランタイムの式エバリュエーターの書き込み | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "式エバリュエーター, チュートリアル"
  - "式の評価のサンプル"
  - "[デバッグ SDK] 式エバリュエーターのデバッグのチュートリアル"
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 共通言語ランタイムの式エバリュエーターの書き込み
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター \(EE\) は、構文を処理するデバッグ エンジン \(DE\) の一部とデバッグ中のコードを生成するプログラミング言語のセマンティクスです。 式は、プログラミング言語のコンテキスト内で評価される必要があります。 たとえば、一部の言語で式の"A \+ B"、"A の合計と B." 他の言語では、同じ式が「A または b.」を可能性があります。 このため、個別の EE 書き込む必要がある Visual Studio IDE でデバッグ対象のオブジェクト コードを生成するプログラミング言語ごとにします。  
  
 Visual Studio のデバッグ パッケージの一部の機能は、プログラミング言語のコンテキストでコードを解釈する必要があります。 ブレークポイントに、ユーザーが入力した任意の式で実行を停止したときなど、 **ウォッチ** ウィンドウを評価して表示する必要があります。 式を入力して、ユーザーがローカル変数の値を変更するさらに、 **ウォッチ** ウィンドウに、 **イミディ エイト** ウィンドウです。  
  
## このセクションの内容  
 [共通言語ランタイムおよび式の評価](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 独自のプログラミング言語は、Visual Studio IDE に統合する、ときに、EE を記述できる独自の言語のコンテキスト内で式を評価する使用するとデバッグ エンジンを記述することがなく、Microsoft intermediate language \(MSIL\) にコンパイルするについて説明します。  
  
 [式エバリュエーターのアーキテクチャ](../../extensibility/debugger/expression-evaluator-architecture.md)  
 EE の必要なインターフェイスを実装し、共通言語ランタイム シンボル プロバイダー \(SP\) とバインダー インターフェイスを呼び出す方法について説明します。  
  
 [式エバリュエーターを登録します。](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 ノート EE 必要があります共通言語ランタイムと Visual Studio のランタイム環境の両方にクラス ファクトリとして自体に登録されています。  
  
 [式エバリュエーターを実装します。](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 式を評価するプロセスがデバッグ エンジン \(DE\)、シンボル プロバイダー \(SP\)、バインダー オブジェクトおよび式エバリュエーター \(EE\) に含まれますについて説明します。  
  
 [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)  
 方法、実行が一時停止時にデバッグ パッケージを呼び出すローカル変数と引数の一覧を取得する DE について説明します。  
  
 [\[ウォッチ\] ウィンドウの式を評価します。](../Topic/Evaluating%20a%20Watch%20Window%20Expression.md)  
 Visual Studio のデバッグ パッケージが、ウォッチ リスト内の各式の現在の値を決定する DE を呼び出す方法について説明します。  
  
 [ローカルの値を変更します。](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 ローカルの値を変更するには、\[ローカル\] ウィンドウの各行が、名前、種類、およびローカルの現在の値を提供する関連付けられたオブジェクトについて説明します。  
  
 [型のビジュアライザーおよびカスタム ビューアーを実装します。](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 型のビジュアライザーとカスタム ビューアーをサポートするコンポーネントによって実装される必要があるインターフェイスについて説明します。  
  
## 参照  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)