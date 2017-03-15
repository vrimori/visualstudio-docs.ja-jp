---
title: "Visual Studio ライブラリの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio ライブラリ、概要"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Visual Studio ライブラリの概要
Visual Studio ではネイティブ C\+\+ ライブラリの VSPackage を簡単に作成するためのテンプレート ベースの C\+\+ クラスです。  Visual Studio のライブラリは C\+\+ のヘッダー ファイルとして完全なソース・コードが含まれます。  ヘッダー ファイルは *Visual Studio SDK インストール パス* \\ VisualStudioIntegration \\ Common \\ ソース CPP \\ \\ \\ にインストール VSL 含まれています。  
  
> [!NOTE]
>  Visual Studio のライブラリはCOM オブジェクト \(ATL\) についての Active Template Library に依存します。  詳細については、「[ATL の概要](/visual-cpp/atl/introduction-to-atl)」を参照してください。  
  
 Visual Studio でライブラリが独自のコードとコードの単体テストをサポートしています。  いくつかの単体テストは次に示すように含まれています :  
  
-   Visual Studio のライブラリの単体テストは *Visual Studio SDK インストール パス* \\ VisualStudioIntegration \\ Common \\ ソース VSL UnitTest に応じて \\ \\ \\ にインストールされます。  
  
-   コードの単体テストの基本クラスは *Visual Studio SDK インストール パス* \\ VisualStudioIntegration \\ Common \\ ソースに応じて VSL \\ \\ INCLUDE \\ VSLUnitTest.h あります。  
  
 一般的に使用される COM インターフェイスと Visual Studio のモック実装はヘッダー ファイルVSLMockSystemInterfaces.h に*Visual Studio SDK インストール パス* \\ VisualStudioIntegration \\ Common \\ \\ にインストール VSLMockVisualStudioInterfaces.h 応じてソースの VSL\\ \\ 含まれています。  
  
## 参照  
 [Visual Studio ライブラリを使用して VSPackages を開発する](../misc/developing-vspackages-by-using-the-visual-studio-library.md)