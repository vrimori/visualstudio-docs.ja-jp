---
title: "C/C++ のコード分析の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "#pragma ディレクティブ, コード分析"
  - "注釈, コード分析"
  - "ビルドの統合, コード分析"
  - "C, コード分析"
  - "C/C++ コード分析"
  - "C++, コード分析"
  - "チェックイン ポリシー, コード分析"
  - "コード分析ツール"
  - "コード分析, C/C++"
  - "コマンド ライン, コード分析"
  - "IDE, コード分析"
  - "pragma ディレクティブ, コード分析"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C/C++ のコード分析の概要
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C\/C\+\+ コード分析ツールは、C\/C\+\+ ソース コードの障害に関する情報を開発者に提供します。  このツールによってレポートされる一般的なコーディング エラーとしては、バッファー オーバーラン、初期化されていないメモリ、null ポインターの逆参照、メモリ リーク、リソース リークなどがあります。  
  
## IDE \(統合開発環境\) の統合  
 開発者の利便性を高めるため、分析ツールは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE に完全に統合されています。  ビルド プロセス中、ソース コードに対して生成された警告はすべて \[エラー一覧\] に表示されます。  警告の原因になったソース コードに移動でき、その問題の原因と解決策に関する追加情報を表示できます。  
  
## \#pragma のサポート  
 `#pragma` ディレクティブを使用することで、開発者は警告をエラーとして扱う、警告の有効と無効を切り替える、または各コード行の警告を表示しないようにすることができます。  詳細については、「[How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/ja-jp/910b8518-71f1-4b2e-b012-70647795642a)」を参照してください。  
  
## 注釈のサポート  
 注釈を使用すると、コード分析がより正確になります。  注釈は、関数のパラメーターおよび戻り値の型に対する Pre 条件および Post 条件について、追加情報を提供します。  詳細については、「[方法: \_\_analysis\_assume を使用して追加のコード情報を指定する](../Topic/How%20to:%20Specify%20Additional%20Code%20Information%20by%20Using%20__analysis_assume.md)」を参照してください。  
  
## チェックイン ポリシーの要件としての分析ツールの実行  
 チェックインされるすべてのソース コードが、特定のポリシーを満たすようにすることが必要になる場合があります。  特に、最新のローカル ビルドのステップとして、分析が確実に実行されているようにすることが必要になる場合があります。  コード分析のチェックイン ポリシーの有効化の詳細については、「[コード分析を用いたチェックイン ポリシーの作成と使用](../code-quality/creating-and-using-code-analysis-check-in-policies.md)」を参照してください。  
  
## チーム ビルドの統合  
 ビルド システムの統合機能を使用すると、コード分析ツールを [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] のビルド処理のステップとして実行できます。  詳細については、「[アプリケーションのビルド](../Topic/Build%20the%20application.md)」を参照してください。  
  
## コマンド ラインのサポート  
 開発者は分析ツールを開発環境から実行する以外に、コマンド ラインから実行することもできます。次にその例を示します。  
  
 `C:\>cl /analyze Sample.cpp`