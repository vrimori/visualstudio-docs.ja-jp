---
title: "デバッグのための言語サービスのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッガーでは、言語のサポート"
  - "デバッグのサポート言語サービス"
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# デバッグのための言語サービスのサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

言語サービスが使用デバッガーをサポートする機能を提供できる、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> インターフェイスです。 これらの機能は、ブレークポイントの検証に式のリストを指定すること、 **\[自動変数\]** ウィンドウです。  
  
 ただし、式エバリュエーターを使用する言語をデバッグしておく必要があります。 式エバリュエーターは、デバッグ中に値を生成する式を評価します。 CLR 式エバリュエーターの実装については、参照してください。  
  
-   [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## コンパイラ出力  
 コンパイラの種類では、言語のデバッグを実行するのに必要なものを決定します。 場合は、コンパイラは、Windows オペレーティング システムを対象とし、プログラムをデバッグするにはデバッグ エンジンを Visual Studio に統合されているネイティブ コードと .pdb ファイルを書き込みます。 コンパイラは、Microsoft 中間言語 \(MSIL\) を生成する場合は、デバッグ エンジンは、Visual Studio に統合されたもマネージ コードでプログラムをデバッグできます。 場合は、コンパイラが独自のオペレーティング システムまたは別のランタイム環境を対象は、独自のデバッグ エンジンを記述する必要があります。  
  
 言語のデバッグの実装の詳細については、次を参照してください。 [作業の開始](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Visual Studio Debugging SDK にします。