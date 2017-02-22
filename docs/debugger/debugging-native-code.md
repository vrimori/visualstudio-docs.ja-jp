---
title: "ネイティブ コードのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [C++], ネイティブ コード"
  - "デバッグ [Visual Studio], ネイティブ コード"
  - "デバッグ (ネイティブ コードを)"
  - "ネイティブ コード, デバッグ"
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ネイティブ コードのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、ネイティブ アプリケーションのデバッグ時に発生する一般的な問題や共通のデバッグ技術について説明します。  ここでは高レベルの手法について説明します。  Visual Studio デバッガーの使用については、「[デバッガーのロードマップ](../debugger/debugger-basics.md)」を参照してください。  
  
## このセクションの内容  
 [方法 : 最適化されたコードをデバッグする](../debugger/how-to-debug-optimized-code.md)  
 最適化されたコードのデバッグに関するヒント、特に、最適化する前のプログラムをデバッグするのが望ましい理由、デバッグ構成とリリース構成の既定の最適化設定、および最適化されたコードにだけ現れるバグを検出するためのヒント \(デバッグ ビルド構成で最適化をオンにする\) を示します。  
  
 [DebugBreak と \_\_debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Win32 関数 `DebugBreak` について説明し、プラットフォーム SDK のリファレンス トピックへのリンクを示します。  また、コンパイラの組み込み関数 `__debugbreak` についても説明します。  
  
 [アサーション](../debugger/c-cpp-assertions.md)  
 アサート ステートメントとそのしくみや利点 \(論理エラーのキャッチ、演算結果のチェック、およびエラー条件のテスト\)、`_DEBUG` との相互作用、および [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でサポートされるアサーションの種類について説明します。  
  
 [方法 :インライン アセンブラー コードをデバッグする](../debugger/how-to-debug-inline-assembly-code.md)  
 \[逆アセンブリ\] ウィンドウを使ってアセンブリ命令を表示する方法および \[レジスタ\] ウィンドウを使ってレジスタの内容を表示する方法について簡単に説明し、これらのウィンドウに関するトピックへのリンクを提供します。  
  
 [MFC のデバッグ技術](../debugger/mfc-debugging-techniques.md)  
 afxDebugBreak、TRACE マクロ、MFC のメモリ リークの検出、MFC アサーション、MFC デバッグ ビルドのサイズの縮小など、MFC プログラムのデバッグ手法について説明するリンクを提供します。  
  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)  
 CRT デバッグ ライブラリの使用、レポート用マクロ、malloc と \_malloc\_dbg の相違、デバッグ用フック関数の作成、CRT デバッグ ヒープなど、C ランタイム ライブラリのデバッグ手法について説明するリンクを提供します。  
  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)  
 Visual C\+\+ プログラムのデバッグに関してよく寄せられる質問とその回答です。  
  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)  
 COM や ActiveX のデバッグに使用できるツールなど、COM アプリケーションや ActiveX アプリケーションのデバッグに関連した情報を提供します。  
  
 [方法: ネイティブ DLL サーバーをデバッグする](../Topic/How%20to:%20Debug%20Native%20DLLs.md)  
 ネイティブ コードから DLL をデバッグする方法について説明します。  
  
 [方法 : 挿入されたコードをデバッグする](../Topic/How%20to:%20Debug%20Injected%20Code.md)  
 属性を使用するコードのデバッグについてのガイダンスを提供します。  ソースの注釈を表示する方法、挿入されたコードを表示する方法、現在の実行ポイントにある逆アセンブリ コードを表示する方法などを説明します。  
  
 [チュートリアル: 並行アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)  
 **\[並列タスク\]** ツール ウィンドウと **\[並列スタック\]** ツール ウィンドウを使用して並行アプリケーションをデバッグする方法について説明します。  
  
## 関連項目  
 [Visual C\+\+ プロジェクトの種類](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Visual C\+\+ プロジェクト テンプレートで作成されたネイティブ プロジェクトをデバッグする方法について説明します。  
  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)  
 デバッグに関連するドキュメントのより広範囲なリンクを提供します。  デバッガーの新機能、設定と準備、ブレークポイント、例外の処理、エディット コンティニュ、マネージ コードのデバッグ、ネイティブ コードのデバッグ、SQL のデバッグ、ユーザー インターフェイス リファレンスなどの情報へのリンクを提供します。  
  
## 参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)