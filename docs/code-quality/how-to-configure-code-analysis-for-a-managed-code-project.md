---
title: '方法: マネージ コード プロジェクトのコード分析を構成する |Microsoft ドキュメント'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 46d41b09f0f6639195613c8a4d9a08f952c79525
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>方法: マネージ コード プロジェクトのコード分析を構成する

Visual Studio では、コード分析の一覧から選択できる*ルール セット*マネージ コード プロジェクトに適用します。 既定の規則セットは*Microsoft 最小推奨規則*です。 ソリューション内の 1 つのプロジェクトまたはすべてのプロジェクトに別の規則セットを適用することもできます。

> [!TIP]
> ASP.NET Web アプリケーションに対して規則セットを構成する方法については、次を参照してください。[する方法: ASP.NET Web アプリケーションのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)です。

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework プロジェクトの規則セットを構成するには

1. 開く、**コード分析**プロジェクトのプロパティ ページのタブです。 これは、次の方法のいずれかで行います。

   - **ソリューション エクスプ ローラー**プロジェクトを選択します。 メニュー バーで、次のように選択します。**分析** > **コード分析を構成する** > **の\<projectname >**です。

   - プロジェクトを右クリックして**ソリューション エクスプ ローラー**を選択し、**プロパティ**、クリックして、**コード分析**タブです。

1. **構成**と**プラットフォーム**一覧で、ビルド構成とターゲット プラットフォームを選択します。

1. 選択した構成を使用して、プロジェクトをビルドするたびにコード分析を実行するには選択、**ビルドに対するコード分析を有効にする**チェック ボックスをオンします。 手動では選択してもコード分析を実行することができます**分析** > **コード分析を実行** > **でコード分析を実行\<projectname >**.

1. 既定では、外部ツールによって自動的に生成されたコードからの警告はコード分析では報告されません。 生成されたコードからの警告を表示するには、オフ、**生成されたコードから結果を表示しない**チェック ボックスをオンします。

    > [!NOTE]
    > コード分析のエラーおよび警告がフォームやテンプレートで表示される場合、このオプションを使用しても、生成されたコードからこのエラーおよび警告の出力は抑制されません。 表示し、上書きされることをしなくても、フォームまたはテンプレートのソース コードを維持します。

1. **この規則セットを実行**ボックスの一覧で、次のいずれかの操作します。

    - 使用する規則セットを選択します。

    - 選択 **\<[参照...] >**既存のカスタム規則セットを見つけるには一覧にします。

    - カスタム規則セットを定義します。 詳細については、次を参照してください。[カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)です。

## <a name="see-also"></a>関連項目

- [チュートリアル: カスタム規則セットの構成と使用](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
- [方法: ASP.NET Web アプリケーション用にコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)