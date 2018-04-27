---
title: C/C++ のコード分析の概要
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ea576ba794350e6cee6b20f8ef9adb62f82a9c51
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="code-analysis-for-cc-overview"></a>C と C++ の概要のコード分析

C/C++ コード分析ツールでは、C/C++ ソース コードの障害に関する情報を提供します。 このツールで報告される一般的なコーディング エラーとして、バッファー オーバーラン、初期化されていないメモリ、Null ポインターの逆参照、メモリ リーク、リソース リークなどがあります。 ツールは、に対してチェックを実行できるもの[C++ コア ガイドライン](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)です。

## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合

コード分析ツールは、Visual Studio IDE 内で完全に統合されています。

ビルド プロセス中にエラー一覧 に、ソース コードの生成された警告が表示されます。 警告の原因となったソース コードに移動することができ、原因と問題の考えられる解決策に関する追加情報を表示することができます。

## <a name="command-line-support"></a>コマンド ライン サポート

次の例で示すように、コマンドラインからの分析ツールを使用することもできます。

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 15.7 およびそれ以降のバージョン**CMake を含むすべてのビルド システムとコマンド ライン ツールを実行することができます。

## <a name="pragma-support"></a>#pragma サポート

使用することができます、`#pragma`警告をエラーとして扱う; を有効にするかを無効にする警告、個別のコード行に警告を抑制するディレクティブ。 詳細については、次を参照してください。[する方法: c/c++ プロジェクトのコード分析プロパティを設定](how-to-set-code-analysis-properties-for-c-cpp-projects.md)です。

## <a name="annotation-support"></a>注釈のサポート

注釈には、コード分析の精度が向上します。 注釈は、関数パラメーターの前と後の状態に関する追加情報を提供し、型を返します。 詳細については、次を参照してください[する方法: _analysis_assume を使用して、追加のコード情報の指定。](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>チェックイン ポリシーの一部として分析ツールを実行します。

すべてソース コードのチェックインが特定のポリシーを満たしていることを必要とする可能性があります。 具体的には、分析に最も最近使用したローカル ビルドのステップとして実行されたことを確認します。 コード分析チェックイン ポリシーを有効にする方法の詳細については、次を参照してください[の作成とコード分析チェックイン ポリシーの使用。](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>チーム ビルドの統合

コード分析ツールのステップとして実行するビルド システムの統合機能を使用することができます、[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]プロセスをビルドします。 詳細については、「[Build and release (ビルドとリリース)](/vsts/build-release/index)」をご覧ください。

## <a name="see-also"></a>関連項目

- [C/c++ コード分析のクイック スタート。](quick-start-code-analysis-for-c-cpp.md)
- [チュートリアル: 障害に対するコードと C/C++ コードを分析します。](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [C/C++ コードの警告に対応するコードの分析](code-analysis-for-c-cpp-warnings.md)
- [C++ Core ガイドライン チェッカーの使用](using-the-cpp-core-guidelines-checkers.md)
- [C++ の主要なガイドライン チェッカー参照](code-analysis-for-cpp-corecheck.md)
- [規則セットを使用して実行対象の C++ 規則を指定する](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [コード分析ツールを使用してドライバー品質を分析します。](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [ドライバー警告のコード分析](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
