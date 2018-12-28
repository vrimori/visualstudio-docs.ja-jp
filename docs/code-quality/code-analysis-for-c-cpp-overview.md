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
ms.openlocfilehash: a1aeb3cea738a08850762083929741c082d7ccb6
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739860"
---
# <a name="code-analysis-for-cc-overview"></a>C と C++ の概要のコード分析

C/C++ コード分析ツールは、C/C++ ソース コードの障害に関する情報を提供します。 このツールで報告される一般的なコーディング エラーとして、バッファー オーバーラン、初期化されていないメモリ、Null ポインターの逆参照、メモリ リーク、リソース リークなどがあります。 ツールは、に対してチェックを実行できることも、 [C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)します。

## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合

コード分析ツールは、Visual Studio IDE 内で完全に統合されています。

ビルド プロセス中には、ソース コードの生成された警告がエラー一覧に表示されます。 警告の原因となったソース コードに移動して、原因と問題の考えられる解決策に関する追加情報を表示できます。

## <a name="command-line-support"></a>コマンド ライン サポート

次の例に示すように、コマンドラインからの分析ツールを使用することもできます。

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 バージョン 15.7 以降**CMake を含むすべてのビルド システムでコマンド ライン ツールを実行することができます。

## <a name="pragma-support"></a>#pragma サポート

使用することができます、`#pragma`ディレクティブは警告をエラーとして扱う; 有効または警告を無効にする個々 の行のコードの警告を非表示にします。 詳細については、「[方法 :C と C++ プロジェクトのコード分析プロパティを設定](how-to-set-code-analysis-properties-for-c-cpp-projects.md)します。

## <a name="annotation-support"></a>注釈のサポート

注釈には、コード分析の精度が向上します。 注釈は、関数のパラメーターの前と後の状態に関する追加情報を提供し、型を返します。 詳細については、「[方法 :_Analysis_assume を使用してコードを追加情報を指定します。](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>分析ツールでは、チェックイン ポリシーの一部として実行します。

すべて元のコードのチェックインが特定のポリシーを満たすことを要求する可能性があります。 具体的には、最新のローカル ビルドのステップとして分析が実行されているかどうかを確認します。 コード分析チェックイン ポリシーを有効にする方法の詳細については、次を参照してください[の作成とコード分析チェックイン ポリシーの使用。](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>チーム ビルドの統合

手順として、コード分析ツールを実行するビルド システムの統合機能を使用することができます、[!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]プロセスを構築します。 詳細については、「[Azure Pipelines](/azure/devops/pipelines/index?view=vsts)」を参照してください。

## <a name="see-also"></a>関連項目

- [クイック スタート:C/C++ のコード分析](quick-start-code-analysis-for-c-cpp.md)
- [チュートリアル: C/C++ コードの分析による障害の](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [C/C++ コードの警告に対応するコードの分析](code-analysis-for-c-cpp-warnings.md)
- [C++ Core ガイドライン チェッカーの使用](using-the-cpp-core-guidelines-checkers.md)
- [C++ Core ガイドライン チェッカーの参照](code-analysis-for-cpp-corecheck.md)
- [規則セットを使用して実行対象の C++ 規則を指定する](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [コード分析ツールを使用して、ドライバーの品質を分析します。](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Code Analysis for Drivers の警告](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
