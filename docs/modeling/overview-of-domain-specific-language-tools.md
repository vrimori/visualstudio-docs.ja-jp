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
ms.openlocfilehash: 6942511e325b77aaa3d646b6e84cd833b8b55ab2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871746"
---
# <a name="overview-of-domain-specific-language-tools"></a>ドメイン固有言語ツールの概要
Visual Studio でホストされている、ドメイン固有言語ツール (DSL ツール) では、ドメイン固有言語を設計し、言語に基づくモデルを作成するユーザーが必要なすべてのものを生成できます。

 DSL ツールでは、次のツールが含まれています。

-   別のソリューション テンプレートを使用して、ドメイン固有言語の開発を始めるのに役立つプロジェクト ウィザード。

-   デザイナーの作成と、ドメイン固有言語定義を編集します。

-   ドメイン固有言語定義が整形式し、問題がある場合は、エラーと警告を表示することを確認する検証エンジン。

-   入力としてドメイン固有言語定義を受け取り、出力としてのソース コードを生成するコード ジェネレーター。

## <a name="the-dsl-tools-solution"></a>DSL ツール ソリューション
 ドメイン固有のデザイナーのウィザードには、次のソリューション テンプレートが用意されています。

- タスク フロー

- クラス ダイアグラム

- 最小言語

- コンポーネント モデル

- 最小限の WPF

- 最小 Windows.Forms

- DSL ライブラリ

  詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートの選択](../modeling/choosing-a-domain-specific-language-solution-template.md)します。

  ウィザードでは、次のプロジェクトを含む Visual Studio ソリューションを作成します。

- Dsl

   Dsl プロジェクトでは、ドメイン固有言語と、編集、および処理ツールを定義します。

- **DslPackage**

   DslPackage プロジェクトでは、言語ツールを Visual Studio と統合する方法を決定します。

## <a name="the-dsl-tools-graphical-interface"></a>DSL ツールのグラフィカル インターフェイス
 DSL ツールのグラフィカル インターフェイスを使用して、ドメイン固有言語に要素および関係を追加することができます。 要素を追加した後は、図形にマップの色のカスタマイズ、デコレータを追加してその外観を定義できます。 ツールボックスに要素を追加することもできます。

## <a name="validation-in-dsl-tools"></a>DSL ツールでの検証
 Dsl は、ドメイン モデルがコード生成のための基本的な要件を満たしているかどうかを確認する検証の 1 つのレベルを提供します。 通常、独自のドメイン固有言語を作成するときに、ビジネス ロジック ルールを表現する独自の検証を追加します。 カスタム検証の詳細については、次を参照してください。[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)です。

 設計する際に多くの場合、ドメイン固有言語を検証することをお勧めします。 ドメイン固有言語には、検証エラーが発生した場合は、ソース コードを生成できません。 クリックして、テンプレートからソース コードを生成するプロセスが実行される**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。 言語の定義を変更するたびにも必ず**すべてのテンプレートの変換**します。 詳細については、次を参照してください。[方法: ドメイン固有言語ソリューションを作成](../modeling/how-to-create-a-domain-specific-language-solution.md)です。

## <a name="customization-of-dsl-tools"></a>DSL ツールのカスタマイズ
 お使いの言語で制約を定義するために、追加のコードをモデルの動作を設定し直すを行うことができます。 必要な場合は、テキスト テンプレートを変更することで大幅な変更を行うことができます。

## <a name="distributing-your-dsl-solution"></a>DSL ソリューションを配布します。
 DSL ツールは、Visual Studio でホストされているパッケージを生成します。 パッケージには、ツールボックス、DSL エクスプ ローラーでは、およびその他のユーザー、ドメイン固有言語を使用してモデルを作成できるようにする UI 要素が表示されます。

 ビルドし、Visual Studio で、DSL Tools のソリューションを実行すると、Visual Studio の 2 番目のインスタンスを表示言語のユーザーに、ドメイン固有言語の検索します。 配布することがすべてが正常に動作することを確認した後、`.vsix`ファイルを DslPackage プロジェクトのビルド フォルダーに表示されます。 他のコンピューター上の Visual Studio 拡張機能として、DSL をインストールするのには、このファイルを使用できます。  詳細については、次を参照してください。[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)します。

## <a name="see-also"></a>関連項目

- [実験用インスタンス](../extensibility/the-experimental-instance.md)
- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)