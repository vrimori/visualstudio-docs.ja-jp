---
title: "CRT デバッグ ライブラリの使用方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "/DEBUG リンカー オプション [C++]"
  - "/LDd コンパイラ関数 [C++]"
  - "/MDd コンパイラ オプション [C++]"
  - "/MTd コンパイラ オプション [C++]"
  - "crtdbg.h ファイル"
  - "デバッグ ライブラリ"
  - "DEBUG リンカー オプション [C++]"
  - "デバッグ [CRT], CRT デバッグ ライブラリ"
  - "LDd コンパイラ関数 [C++]"
  - "ライブラリ, CRT デバッグ ライブラリ"
  - "MDd コンパイラ オプション [C++]"
  - "MTd コンパイラ オプション [C++]"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# CRT デバッグ ライブラリの使用方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C ランタイム ライブラリには、広範なデバッグ支援機能が用意されています。  CRT デバッグ ライブラリを使用するには、[\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info) を指定してリンクし、**\/MDd**、**\/MTd**、または **\/LDd** を指定してコンパイルする必要があります。  
  
## 解説  
 CRT のデバッグに使用する主な定義とマクロは、CRTDBG.h ヘッダー ファイルに記述されています。  
  
 CRT デバッグ ライブラリの関数は、デバッグ情報 \([\/Z7、\/Zd、\/Zi、\/ZI](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) オプションで指定\) を含んだ状態で、最適化されずにコンパイルされています。  渡されるパラメーターを検証するためのアサート ステートメントを含む関数もあり、これらの関数のソース コードは公開されています。  このソース コードを利用すると、CRT 関数をステップ実行して、その関数が正常に動作しているかを確認したり、パラメーターやメモリ状態が不正でないかどうかを検証したりできます。 一部の CRT 技術については権利が保有されており、例外処理、浮動小数点数、その他いくつかのルーチンのソース コードは公開されていません。  
  
 Visual C\+\+ をインストールするときに、C ランタイム ライブラリのソース コードをハード ディスクにインストールするかどうかを選択できます。  ソース コードをインストールしない場合は、CRT 関数をステップ実行するときに CD\-ROM が必要になります。  
  
 使用できる各種ランタイム ライブラリの詳細については、「[C ランタイム ライブラリ](/visual-cpp/c-runtime-library/crt-library-features)」を参照してください。  
  
## 参照  
 [CRT のデバッグ技術](../debugger/crt-debugging-techniques.md)   
 [\/MD、\/MT、\/LD \(ランタイム ライブラリの使用\)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)