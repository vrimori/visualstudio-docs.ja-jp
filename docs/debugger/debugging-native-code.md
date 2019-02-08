---
title: ネイティブ コードのデバッグ |Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9b057d10e03274186160fc468da8fbc7714ffe14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034078"
---
# <a name="debugging-native-code"></a>ネイティブ コードのデバッグ
ここでは、ネイティブ アプリケーションのデバッグ時に発生する一般的な問題や共通のデバッグ技術について説明します。 ここでは高レベルの手法について説明します。 Visual Studio デバッガーの使用のしくみを参照してください。[デバッガーでのはじめ](../debugger/debugger-feature-tour.md))。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 最適化されたコードをデバッグする](../debugger/how-to-debug-optimized-code.md)  
 最適化されたコードのデバッグに関するヒント、特に、最適化する前のプログラムをデバッグするのが望ましい理由、デバッグ構成とリリース構成の既定の最適化設定、および最適化されたコードにだけ現れるバグを検出するためのヒント (デバッグ ビルド構成で最適化をオンにする) を示します。  
  
 [DebugBreak と __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Win32 関数 `DebugBreak` について説明し、プラットフォーム SDK のリファレンス トピックへのリンクを示します。 また、コンパイラの組み込み関数 `__debugbreak` についても説明します。  
  
 [C/C++ アサーション](../debugger/c-cpp-assertions.md)  
 アサート ステートメントとそのしくみや利点 (論理エラーのキャッチ、演算結果のチェック、およびエラー条件のテスト)、`_DEBUG` との相互作用、および [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でサポートされるアサーションの種類について説明します。  
  
 [方法: インライン アセンブラー コードをデバッグする](../debugger/how-to-debug-inline-assembly-code.md)  
 [逆アセンブリ] ウィンドウを使ってアセンブリ命令を表示する方法および [レジスタ] ウィンドウを使ってレジスタの内容を表示する方法について簡単に説明し、これらのウィンドウに関するトピックへのリンクを提供します。  
  
 [MFC のデバッグ技術](../debugger/mfc-debugging-techniques.md)  
 afxDebugBreak、TRACE マクロ、MFC のメモリ リークの検出、MFC アサーション、MFC デバッグ ビルドのサイズの縮小など、MFC プログラムのデバッグ手法について説明するリンクを提供します。  
  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)  
 CRT デバッグ ライブラリの使用、レポート用マクロ、malloc と _malloc_dbg の相違、デバッグ用フック関数の作成、CRT デバッグ ヒープなど、C ランタイム ライブラリのデバッグ手法について説明するリンクを提供します。  
  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)  
 Visual C++ プログラムのデバッグに関してよく寄せられる質問とその回答です。  
  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)  
 COM や ActiveX のデバッグに使用できるツールなど、COM アプリケーションや ActiveX アプリケーションのデバッグに関連した情報を提供します。  
  
 [方法: 挿入されたコードをデバッグする](../debugger/how-to-debug-injected-code.md)  
 属性を使用するコードのデバッグについてのガイダンスを提供します。 ソースの注釈を表示する方法、挿入されたコードを表示する方法、現在の実行ポイントにある逆アセンブリ コードを表示する方法などを説明します。  
  
 [チュートリアル: 並列アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)  
 **[並列タスク]** ツール ウィンドウと **[並列スタック]** ツール ウィンドウを使用して並行アプリケーションをデバッグする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Visual C++ プロジェクトの種類](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Visual C++ プロジェクト テンプレートで作成されたネイティブ プロジェクトをデバッグする方法について説明します。  

 [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)ネイティブおよびマネージ Dll をデバッグする方法について説明します。
  
 [デバッガーでのはじめに](../debugger/debugger-feature-tour.md)  
 デバッグに関連するドキュメントのより広範囲なリンクを提供します。 デバッガーの新機能、設定と準備、ブレークポイント、例外の処理、エディット コンティニュ、マネージド コードのデバッグ、ネイティブ コードのデバッグ、SQL のデバッグ、ユーザー インターフェイス リファレンスなどの情報へのリンクを提供します。  
  
## <a name="see-also"></a>関連項目
 [デバッガーのセキュリティ](../debugger/debugger-security.md)  
 [Visual Studio でのデバッグ](../debugger/index.md) 
