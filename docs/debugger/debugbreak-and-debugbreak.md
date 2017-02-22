---
title: "DebugBreak と __debugbreak | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "ブレークポイント, DebugBreak 関数"
  - "DebugBreak 関数"
  - "デバッグ [C++], DebugBreak 関数"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DebugBreak と __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DebugBreak Win32 関数または [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) 組み込み関数は、コード内のどこからでも呼び出すことができます。  `DebugBreak` および `__debugbreak` を呼び出した場合の動作は、その位置にブレークポイントを設定した場合と同様です。  
  
 `DebugBreak` はシステム関数の呼び出しであるため、システム デバッグ シンボルをインストールして、中断の後に正しい呼び出し履歴情報が表示されるようにする必要があります。  そうしなかった場合、デバッガーによって表示される呼び出し履歴情報は、1 フレームずれて表示されることがあります。  `__debugbreak` を使用した場合、シンボルは不要です。  
  
## 参照  
 [コンパイラ組み込み](/visual-cpp/intrinsics/compiler-intrinsics)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)