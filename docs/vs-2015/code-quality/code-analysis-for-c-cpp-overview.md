---
title: コード分析を使用した C++ の概要について |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 27
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6764e39d55ebe2ce11776035f25d6fdf69be081
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545635"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ のコード分析の概要
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Code Analysis for C と C++ の概要](https://docs.microsoft.com/visualstudio/code-quality/code-analysis-for-c-cpp-overview)します。  
  
C/C++ コード分析ツールは、C/C++ ソース コードの障害に関する情報を開発者に提供します。 このツールによってレポートされる一般的なコーディング エラーとしては、バッファー オーバーラン、初期化されていないメモリ、null ポインターの逆参照、メモリ リーク、リソース リークなどがあります。  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合  
 開発者分析ツールを使用する自然に完全に統合内で、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE。 ビルド プロセス中には、ソース コードの生成された警告がエラー一覧に表示されます。 警告の原因となったソース コードに移動して、原因と問題の考えられる解決策に関する追加情報を表示できます。  
  
## <a name="pragma-support"></a>#pragma サポート  
 開発者が使用できる、`#pragma`ディレクティブは警告をエラーとして扱う; 有効または警告を無効にする個々 の行のコードの警告を非表示にします。 詳細については、次を参照してください。[方法: 有効にすると特定の警告を C と C++ のコード分析を無効にする](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a)します。  
  
## <a name="annotation-support"></a>注釈のサポート  
 注釈には、コード分析の精度が向上します。 注釈は、関数のパラメーターの前と後の状態に関する追加情報を提供し、型を返します。 詳細については、次を参照してください[方法: _analysis_assume を使用して追加のコード情報の指定。](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>分析ツールでは、チェックイン ポリシーの一部として実行します。  
 すべて元のコードのチェックインが特定のポリシーを満たすことを要求する可能性があります。 具体的には、最新のローカル ビルドのステップとして分析が実行されているかどうかを確認します。 コード分析チェックイン ポリシーを有効にする方法の詳細については、次を参照してください[の作成とコード分析チェックイン ポリシーの使用。](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>チーム ビルドの統合  
 手順として、コード分析ツールを実行するビルド システムの統合機能を使用することができます、[!INCLUDE[esprtfs](../includes/esprtfs-md.md)]プロセスを構築します。 詳細については、「[アプリケーションのビルド](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)」をご覧ください。  
  
## <a name="command-line-support"></a>コマンド ライン サポート  
 開発環境内で完全な統合、に加えて開発者できますも分析ツールを使用、コマンドラインから次の例に示すように。  
  
 `C:\>cl /analyze Sample.cpp`



