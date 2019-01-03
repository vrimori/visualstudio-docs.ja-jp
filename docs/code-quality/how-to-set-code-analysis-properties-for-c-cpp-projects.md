---
title: '方法: C/C++ プロジェクトのコード分析プロパティを設定する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 000b731bffe6b2fe02e34e98ebfd3ce8a21f5bd8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915631"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>方法: C/C++ プロジェクトのコード分析プロパティを設定する
コード分析ツールは、プロジェクトの各構成でコード分析を使用してルールを構成できます。 さらに、生成され、サード パーティ製ツールを使用して、プロジェクトに追加されたコードからの警告を抑制するコード分析を指示することができます。

## <a name="code-analysis-property-page"></a>コード分析 プロパティ ページ
 **コード分析**プロパティ ページには、プロジェクトのすべてのコード分析の構成設定が含まれています。 プロジェクトのコード分析プロパティ ページを開く**ソリューション エクスプ ローラー**プロジェクトを右クリックし、クリックして**プロパティ**します。 次に、展開**構成プロパティ**を選択し、**コード分析**タブ。

## <a name="project-configuration-and-platform"></a>プロジェクト構成とプラットフォーム
 **構成**一覧と**プラットフォーム**の一覧を使用して、プロジェクトの構成とプラットフォームの組み合わせに別のコード分析設定を適用できます。 たとえば、プロジェクトをデバッグする 1 つの一連のルールを適用するコード分析のビルドし、リリースの別のセットを作成を指示できます。

## <a name="enabling-code-analysis"></a>コード分析を有効にします。
 選択して、プロジェクトのコード分析を有効にするかどうかを決定できます**を有効にするコード分析の C/C++ ビルドの**します。 組み合わせて、**構成** ボックスの一覧、たとえば、ことがデバッグ ビルドとリリース ビルドを有効にするコード分析を無効にします。

 プロジェクトにマネージ コードが含まれている場合は、有効にするか選択してコード分析を無効にするかどうかを決定**ビルドに対するコード分析を有効にする**します。

 コード分析は、コードの品質を向上させるし、よくある落とし穴の回避に役立つ設計されています。 そのため、慎重に検討すると、コード分析を無効にするかどうか。 通常、ルール セットを無効にすることをお勧めまたはしないようにする個々 のルールは、プロジェクトに適用します。

## <a name="generated-code"></a>生成されたコード
 開発者は、アプリケーションを迅速に開発を支援するのにツールを頻繁に使用します。 これらのツールは、プロジェクトに追加されるコードを生成できます。 コード分析が生成されたコードで検出する規則違反を確認する場合があります。 ただし、コードを維持したくない場合に参照しない可能性があります。

 **から生成されたコードの結果を抑制する**チェック ボックスをオン、**全般**プロパティ ページをサード パーティのツールによって生成されるマネージ コードからのコード分析の警告を表示するかどうかを選択することができます.

## <a name="rule-sets"></a>規則セット
 ルール セットを選択して、コード分析で適用する規則を選択できますが、プロジェクトにマネージ コードが含まれている場合、**この規則セットを実行**一覧。

## <a name="see-also"></a>関連項目

- [マネージド コードの品質の分析](../code-quality/code-analysis-for-managed-code-overview.md)
- [C/C++ コードの警告に対応するコードの分析](../code-quality/code-analysis-for-c-cpp-warnings.md)