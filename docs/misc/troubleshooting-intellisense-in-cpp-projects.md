---
title: "C++ プロジェクトでの IntelliSense のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ncb ファイル"
  - "IntelliSense, トラブルシューティング (C++ プロジェクトでの失敗)"
  - "ncb ファイル"
  - "トラブルシューティング (IntelliSense)"
  - "トラブルシューティング (Visual C++), IntelliSense"
ms.assetid: 72e4eb39-66d3-403d-8da7-00ed288a1899
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# C++ プロジェクトでの IntelliSense のトラブルシューティング
IntelliSense は、特定の状況で動作が停止することがあります。  次の手順で、IntelliSense が C\+\+ プロジェクトで動作しない理由を判断してください。  
  
### C\+\+ プロジェクトでの IntelliSense のエラーを調査するには  
  
1.  Visual C\+\+ プロジェクトにコンパイル エラーがないことを確認します。  
  
    1.  プロジェクトがメイクファイル プロジェクトの場合は、「[方法 : メイクファイル プロジェクトで IntelliSense を使用可能にする](../Topic/How%20to:%20Enable%20IntelliSense%20for%20Makefile%20Projects.md)」を参照してください。  
  
2.  stdafx.h がインクルード パスに含まれていることを確認します。  Visual C\+\+ プロジェクトのインクルード パスの詳細については、「[\#include ディレクティブ](/visual-cpp/preprocessor/hash-include-directive-c-cpp)」および「[\/I \(追加インクルード ディレクトリ\)](/visual-cpp/build/reference/i-additional-include-directories)」を参照してください。  
  
## IntelliSense の制約  
 IntelliSense は、次の状況では C\+\+ プロジェクトで動作しません。  
  
-   カーソルがコード コメント内にある場合。  
  
-   リテラル文字列を作成している場合。  
  
-   構文エラーがカーソルの上部に表示されている場合。  
  
-   ソリューションは、マネージ C\+\+ の構文、または以前の C\+\+ マネージ拡張構文で構成されます。  
  
-   `#include` ディレクティブを使用してヘッダー ファイルを複数回参照した場合、および `#define` ディレクティブを介して定義されているマクロのさまざまな状態が原因となって、そのヘッダー ファイルの意味が変更される場合は、IntelliSense は完全にはサポートされません。  つまり、マクロの状態に応じてヘッダーの使用法が変わるヘッダー ファイルを複数回インクルードすると、IntelliSense は必ずしも機能しません。  
  
## 参照  
 [Troubleshooting IntelliSense](http://msdn.microsoft.com/ja-jp/c1b3adb9-0d48-4770-a51e-392ed818c484)   
 [方法 : ビルドのプロジェクト出力ファイルを編成する](../Topic/How%20to:%20Organize%20Project%20Output%20Files%20for%20Builds.md)