---
title: "Visual C++ でのデバッグ機能の使用 (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
helpviewer_keywords: 
  - "/D_DEBUG コンパイラ オプション [C++]"
  - "_DEBUG マクロ"
  - "アサーション, 有効化 (デバッグ機能を)"
  - "D_DEBUG コンパイラ オプション"
  - "デバッグ ビルド, MFC"
  - "デバッグ [C++], 有効化 (デバッグ機能を)"
  - "デバッグ [MFC], 有効化 (デバッグ機能を)"
  - "MFC ライブラリ, デバッグ バージョン"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visual C++ でのデバッグ機能の使用 (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] では、シンボル **\_DEBUG** を定義してプログラムをコンパイルすると、アサーションなどのデバッグ機能が有効になります。  **\_DEBUG** は、次のいずれかの方法で定義できます。  
  
-   ソース コードで **\#define \_DEBUG** を指定します。または  
  
-   **\/D\_DEBUG** コンパイラ オプションを指定します  \(Visual Studio のウィザードを使用してプロジェクトを作成した場合は、デバッグ構成で **\/D\_DEBUG** が自動的に定義されます\)。  
  
 **\_DEBUG** を定義すると、コンパイラでは **\#ifdef \_DEBUG** と `#endif` で囲まれたコードのセクションがコンパイルされます。  
  
 MFC プログラムのデバッグ構成は、MFC ライブラリのデバッグ バージョンとリンクする必要があります。  MFC ヘッダー ファイルは、**\_DEBUG** や **\_UNICODE** など、定義済みのシンボルに基づいて、リンクする MFC ライブラリの適正なバージョンを判定します。  詳細については、「[MFC ライブラリのバージョン](/visual-cpp/mfc/mfc-library-versions)」を参照してください。  
  
## 参照  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)