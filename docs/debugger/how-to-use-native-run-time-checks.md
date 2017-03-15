---
title: "方法 : ネイティブ ランタイム チェックを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.errorchecks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/O コンパイラ オプション, /RTC オプション"
  - "/RTC コンパイラ オプション [C++], /O コンパイラ オプション"
  - "配列 [Visual Studio], デバッグ"
  - "デバッガー, ネイティブ ランタイム チェック"
  - "デバッガー, ランタイム エラー"
  - "デバッグ (配列を)"
  - "ネイティブ ランタイム チェック"
  - "O コンパイラ オプション, /RTC オプション"
  - "最適化されたビルド オプション"
  - "RTC コンパイラ オプション, /O コンパイラ オプション"
  - "ランタイム チェック"
  - "ランタイム チェック, native"
  - "ランタイム エラー, デバッグ"
  - "ランタイム エラー, エラー チェック"
  - "runtime_checks プラグマ"
  - "スタック ポインター"
  - "スタック ポインター, 破損"
  - "スタック, ポインターの破損"
  - "変数 [デバッガー], キャッチ (初期化されていないローカル変数の依存関係を)"
  - "変数 [デバッガー], 損失 (データの)"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 方法 : ネイティブ ランタイム チェックを使用する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual C\+\+ では、ネイティブ [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) を使用して、次のような一般的なランタイム エラーをキャッチできます。  
  
-   スタック ポインターの破損  
  
-   ローカル配列のオーバーラン  
  
-   スタックの破損  
  
-   初期化されていないローカル変数への依存性  
  
-   短い変数への代入によるデータの消失  
  
 最適化された \(**\/RTC**\) ビルドで **\/O** を使用すると、コンパイラ エラーが発生します。`runtime_checks` プラグマを最適化されたビルドに使用しても効果はありません。  
  
 ランタイム チェックが有効になっている状態のプログラムをデバッグすると、既定の動作では、ランタイム エラーの発生時にプログラムが停止し、デバッガーが起動されます。 この既定の動作は、任意のランタイム チェックで変更できます。 詳細については、「[デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)」を参照してください。  
  
 次の手順で、デバッグ ビルドでネイティブ ランタイム チェックを有効にする方法と、ネイティブ ランタイム チェックの動作を変更する方法を説明します。  
  
 このセクションのその他のトピックでは、次の内容について説明します。  
  
-   [C ランタイム ライブラリによるネイティブ ランタイム チェックのカスタマイズ](../debugger/native-run-time-checks-customization.md)  
  
-   [C ランタイム ライブラリなしのランタイム チェックの使用方法](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### デバッグ ビルドでネイティブ ランタイム チェックを有効にするには  
  
-   **\/RTC** オプションを使用して、C ランタイム ライブラリのデバッグ バージョン \(\/MDd など\) とリンクします。  
  
### ネイティブ ランタイム チェックの動作を変更するには  
  
-   `runtime_checks` プラグマを使用します。  
  
## 参照  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [ランタイム エラー チェック](/visual-cpp/c-runtime-library/run-time-error-checking)