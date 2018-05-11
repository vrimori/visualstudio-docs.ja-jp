---
title: Visual Studio でコード分析を構成します。
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: afa7a75ae083133f2cff1197b2aa111a1d7bf719
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>方法: マネージ コード プロジェクトのコード分析を構成する

Visual Studio では、コード分析の一覧から選択できる*ルール セット*マネージ コード プロジェクトに適用します。 既定の規則セットは*Microsoft 最小推奨規則*です。 ソリューション内の 1 つのプロジェクトまたはすべてのプロジェクトに別の規則セットを適用することもできます。

> [!TIP]
> ASP.NET Web アプリケーションに対して規則セットを構成する方法については、次を参照してください。[する方法: ASP.NET Web アプリケーションのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)です。

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>.NET Framework プロジェクトの規則セットを構成するには

1. 開く、**コード分析**プロジェクトのプロパティ ページのタブです。 これは、次の方法のいずれかで行います。

   - **ソリューション エクスプ ローラー**プロジェクトを選択します。 メニュー バーで、次のように選択します。**分析** > **コード分析を構成する** > **の\<projectname >** です。

   - プロジェクトを右クリックして**ソリューション エクスプ ローラー**を選択し、**プロパティ**、クリックして、**コード分析**タブです。

1. **構成**と**プラットフォーム**一覧で、ビルド構成とターゲット プラットフォームを選択します。

1. 選択した構成を使用して、プロジェクトをビルドするたびにコード分析を実行するには選択、**ビルドに対するコード分析を有効にする**チェック ボックスをオンします。 手動では選択してもコード分析を実行することができます**分析** > **コード分析を実行** > **でコード分析を実行\<projectname >**.

1. 既定では、外部ツールによって自動的に生成されたコードからの警告はコード分析では報告されません。 生成されたコードからの警告を表示するには、オフ、**生成されたコードから結果を表示しない**チェック ボックスをオンします。

    > [!NOTE]
    > コード分析のエラーおよび警告がフォームやテンプレートで表示される場合、このオプションを使用しても、生成されたコードからこのエラーおよび警告の出力は抑制されません。 表示し、上書きされることをしなくても、フォームまたはテンプレートのソース コードを維持します。

1. **この規則セットを実行**ボックスの一覧で、次のいずれかの操作します。

    - 使用する規則セットを選択します。

    - 選択 **\<[参照...] >** 既存のカスタム規則セットを見つけるには一覧にします。

    - 定義、[カスタム規則セット](../code-quality/how-to-create-a-custom-rule-set.md)です。

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>ソリューション内の複数のプロジェクトに対して規則セットを指定します。

既定では、ソリューションのすべてのマネージ プロジェクトが割り当てられている、 *Microsoft 最小推奨規則*コード分析規則セットです。 ソリューションのプロジェクトに割り当てられている規則セットを変更することができます、**プロパティ**ソリューションのダイアログ ボックス。

1. Visual Studio でソリューションを開きます。

2. **分析**メニューの **ソリューションのコード分析を構成する**です。

3. 必要に応じて、展開**共通プロパティ**、し、**コード分析設定**です。

4. 1 つまたは複数のプロジェクトに対して規則セットを指定できます。

    - 個々 のプロジェクトに対して規則セットを指定するには、プロジェクト名を選択します。

    - 押しながら複数のプロジェクトに対して規則セットを指定する**Ctrl**プロジェクト名を選択します。

    - ソリューション内のすべてのプロジェクトを指定するにを押しながら**shift キーを押し**プロジェクトの一覧でをクリックします。

5. 選択、**ルール セットの**プロジェクトのフィールドと ルールのセットの名前を適用することです。

## <a name="see-also"></a>関連項目

- [方法: ASP.NET Web アプリケーション用にコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)