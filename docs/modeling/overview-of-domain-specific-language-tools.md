---
title: ドメイン固有言語ツールの概要
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d64c819e1d07fed44372edca2c7107d956937d58
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949525"
---
# <a name="overview-of-domain-specific-language-tools"></a>ドメイン固有言語ツールの概要
ホストされるドメイン固有言語ツール (DSL ツール)[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]では、ドメイン固有言語の設計および言語に基づくモデルを作成するためのユーザーが必要なすべてのものを生成します。

 DSL ツールでは、次のツールが含まれています。

-   ドメイン固有言語の開発を開始するために別のソリューション テンプレートを使用するプロジェクト ウィザード。

-   作成して、ドメイン固有言語定義を編集するためのグラフィカルなデザイナーです。

-   ドメイン固有言語の定義が整形式では、し、問題がある場合に、エラーおよび警告を表示する検証エンジン。

-   入力として、ドメイン固有言語定義を受け取り、出力としてソース コードを生成するコード ジェネレーター。

## <a name="the-dsl-tools-solution"></a>DSL ツールのソリューション
 ドメイン固有のデザイナーのウィザードには、次のソリューション テンプレートが用意されています。

-   タスク フロー

-   クラス ダイアグラム

-   最小限の言語

-   コンポーネント モデル

-   最小限の WPF

-   最小 Windows.Forms

-   DSL ライブラリ

 詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートを選択する](../modeling/choosing-a-domain-specific-language-solution-template.md)です。

 ウィザードで作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]次のプロジェクトが含まれるソリューション。

-   Dsl

     Dsl プロジェクトでは、ドメイン固有言語と、編集および処理ツールを定義します。

-   **DslPackage**

     言語のツールを統合する方法を決定 DslPackage プロジェクト[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。

## <a name="the-dsl-tools-graphical-interface"></a>DSL ツールのグラフィカル インターフェイス
 DSL ツールのグラフィカル インターフェイスを使用するには、ドメイン固有言語に要素および関係を追加します。 要素を追加した後は、図形にマッピングすること、色のカスタマイズ、およびデコレーターを追加することによって、外観を定義できます。 ツールボックスに要素を追加することもできます。

## <a name="validation-in-dsl-tools"></a>DSL ツールでの検証
 Dsl は、ドメイン モデルがコード生成のための基本的な要件を満たしているかどうかを確認する検証の 1 つのレベルを提供します。 通常、独自のドメイン固有言語を作成するときに、ビジネス ロジック ルールを表現する独自の検証を追加します。 カスタム検証の詳細については、次を参照してください。[ドメイン固有言語で検証](../modeling/validation-in-a-domain-specific-language.md)です。

 設計する際に多くの場合、ドメイン固有言語を検証することをお勧めします。 ドメイン固有言語には、検証エラーが発生した場合は、ソース コードを生成できません。 クリックして、テンプレートからソース コードを生成するプロセスが実行される**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバーにします。 言語の定義を変更するたびにも必ず**すべてのテンプレートの変換**です。 詳細については、次を参照してください。[する方法: ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)です。

## <a name="customization-of-dsl-tools"></a>DSL ツールのカスタマイズ
 モデルの動作を設定し直すと、言語で制約を定義するための追加のコードを提供できます。 必要な場合は、テキスト テンプレートを変更することで大幅な変更をすることができます。

## <a name="distributing-your-dsl-solution"></a>DSL ソリューションを配布します。
 DSL ツールでホストされているパッケージを生成する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 パッケージには、ツールボックス、DSL のエクスプ ローラーでは、およびその他のユーザーが、ドメイン固有言語を使用してモデルを作成できる UI 要素が表示されます。

 ビルドおよび DSL ツールのソリューションを実行するときに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、2 番目のインスタンスの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ドメイン固有言語が言語のユーザーに表示する方法を示しています。 すべてが正常に動作することを確認する後に割り当てることができます、`.vsix`ファイル DslPackage プロジェクトのビルド フォルダーに表示されます。 このファイルを使用して、インストールとして DSL、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]他のコンピューター上の拡張機能です。  詳細については、次を参照してください。[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)です。

## <a name="see-also"></a>関連項目

- [実験用インスタンス](../extensibility/the-experimental-instance.md)
- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)