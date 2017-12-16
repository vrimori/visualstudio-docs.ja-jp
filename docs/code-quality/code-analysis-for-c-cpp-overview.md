---
title: "コード分析の概要については C と C++ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1634250d97e83b21cccd3ada90933fc0806d35f
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ のコード分析の概要
C/C++ コード分析ツールは、C/C++ ソース コードの障害に関する情報を開発者に提供します。 このツールによってレポートされる一般的なコーディング エラーとしては、バッファー オーバーラン、初期化されていないメモリ、null ポインターの逆参照、メモリ リーク、リソース リークなどがあります。  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合  
 開発者分析ツールを使用する自然するために、完全に統合されて内で、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE です。 ビルド プロセス中にエラー一覧 に、ソース コードの生成された警告が表示されます。 警告の原因となったソース コードに移動することができ、原因と問題の考えられる解決策に関する追加情報を表示することができます。  
  
## <a name="pragma-support"></a>#pragma サポート  
 開発者が使用できる、`#pragma`警告をエラーとして扱う; を有効にするかを無効にする警告、個別のコード行に警告を抑制するディレクティブ。 詳細については、次を参照してください。[する方法: c/c++ プロジェクトのコード分析プロパティを設定](how-to-set-code-analysis-properties-for-c-cpp-projects.md)です。  
  
## <a name="annotation-support"></a>注釈のサポート  
 注釈には、コード分析の精度が向上します。 注釈は、関数パラメーターの前と後の状態に関する追加情報を提供し、型を返します。 詳細については、次を参照してください[する方法: _analysis_assume を使用して、追加のコード情報の指定。](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>チェックイン ポリシーの一部として分析ツールを実行します。  
 すべてソース コードのチェックインが特定のポリシーを満たしていることを必要とする可能性があります。 具体的には、分析に最も最近使用したローカル ビルドのステップとして実行されたことを確認します。 コード分析チェックイン ポリシーを有効にする方法の詳細については、次を参照してください[の作成とコード分析チェックイン ポリシーの使用。](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>チーム ビルドの統合  
 コード分析ツールのステップとして実行するビルド システムの統合機能を使用することができます、[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]プロセスをビルドします。 詳細については、「[アプリケーションのビルド](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)」をご覧ください。  
  
## <a name="command-line-support"></a>コマンド ライン サポート  
 だけでなく、完全統合開発環境では、開発者も行えます分析ツールをコマンドラインから次の例で示すように。  
  
 `C:\>cl /analyze Sample.cpp`