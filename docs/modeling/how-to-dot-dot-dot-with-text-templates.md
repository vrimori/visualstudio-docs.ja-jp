---
title: テキスト テンプレートでどうやって ... をする
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9d9a1826e8c06d947e05bf7201f2963a7bac860f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039580"
---
# <a name="how-to--with-text-templates"></a>テキスト テンプレートでどうやって ... をする
Visual Studio のテキスト テンプレートは、あらゆる種類のテキストを生成するのに便利な方法を提供します。 テキスト テンプレートを使用すると、アプリケーションの一部として実行時にテキストを生成したり、デザイン時にプロジェクト コードの一部を生成することができます。 このトピックでは、「どうやって ... をするか？」として最も頻繁に寄せられる質問をまとめています。

 このトピックでは、ビュレットが付いている複数の回答は代替案です。

 テキスト テンプレートの一般的な概要については、[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)をお読みください。

## <a name="how-to-"></a>どうやって ... をする

### <a name="generate-part-of-my-application-code"></a>アプリケーション コードの一部を生成
 ファイルまたはデータベースにコンフィグレーションまたは*モデル*があります。 コードの 1 つ以上の部分が、そのモデルに依存しています。

-   テキスト テンプレートから、コード ファイルの一部を生成します。 詳細については、[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)と[テンプレートの作成を開始する最善の方法は何ですか?](#starting)を参照してください。

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>テンプレートにデータを渡して、実行時にファイルを生成する。

-   ランタイム テキスト テンプレートをプロジェクトに追加します。 このテンプレートは、あなたのコードでインスタンス化しテキストを生成することができるクラスを作成します。 データは、コンストラクターのパラメーターから渡すことができます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)

-   実行時にのみ使用可能なテンプレートを生成する場合は、標準のテキスト テンプレートを使用できます。 Visual Studio 拡張機能を作成する場合は、テキスト テンプレート サービスを呼び出すことができます。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md) 他のコンテキストで、テキスト テンプレート エンジンを使用することができます。 詳細については、「 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 」を参照してください。

     パラメーターをこれらのテンプレートに渡すには \<#@parameter#> ディレクティブを使用します。 詳細については、次を参照してください。 [T4 パラメーター ディレクティブ](../modeling/t4-parameter-directive.md)

### <a name="read-another-project-file-from-a-template"></a>テンプレートから別のプロジェクト ファイルを読み取る
 テンプレートと同じ Visual Studio プロジェクトからのファイルを読み取るには次のようにします。

-   `hostSpecific="true"` ディレクティブに `<#@template#>` を挿入します。

     コードで、ファイルの完全なパスを取得するために、`this.Host.ResolvePath(filename)` を使用します。

### <a name="invoke-methods-from-a-template"></a>テンプレートからメソッドを呼び出す
 標準[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .NET Framework クラスなど、既に存在するメソッドの場合:

- \<#@assembly#> ディレクティブを使用して、アセンブリをロードし、\<#@import#> を使用して名前空間のコンテキストを設定します。 詳細については、次を参照してください。 [T4 インポート ディレクティブ](../modeling/t4-import-directive.md)

   頻繁に同じアセンブリのセットを使用し、ディレクティブをインポートする場合には、ディレクティブ プロセッサの作成を検討してください。 各テンプレートでは、アセンブリとモデル ファイルを読み込み、名前空間のコンテキストを設定できるディレクティブ プロセッサを呼び出すことができます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)

  自分で作成したメソッドの場合:

- ランタイム テキスト テンプレートを作成する場合、ランタイム テキスト テンプレートと同じ名前を持つ部分クラス定義を記述します。 このクラスに、追加するメソッドを追加します。

- メソッド、プロパティ、およびプライベートのクラス宣言ができるクラス機能コントロール ブロック `<#+ ... #>` を書きます。 そのテキスト テンプレートはコンパイル時に、クラスに変換されます。 標準コントロール ブロック `<#...#>` とテキストは、1 つのメソッドに変換され、クラス機能ブロックは別のメンバーとして挿入されます。 詳細については、次を参照してください。[テキスト テンプレートのコントロール ブロック](../modeling/text-template-control-blocks.md)

   クラスの機能として定義されたメソッドは、埋め込みのテキスト ブロックとして含めることもできます。

   別のファイルにクラスの機能を配置すること検討します。`<#@include#>` で1 つまたは複数のテンプレート ファイルにインクルードするこができます。

- 別のアセンブリ (クラス ライブラリ) で、メソッドを記述し、テンプレートから呼び出します。 `<#@assembly#>` ディレクティブを使用してアセンブリを読み込み、`<#@import#>` を使用して名前空間のコンテキストを設定します。 デバッグによりアセンブリを再構築するには、Visual Studio を停止し再起動する必要があることに注意してください。 詳細については、次を参照してください。 [T4 テキスト テンプレート ディレクティブ](../modeling/t4-text-template-directives.md)

### <a name="generate-many-files-from-one-model-schema"></a>1 つのモデル スキーマからの多数のファイル生成
 ファイルを生成するには、同じ XML またはデータベース スキーマを持つモデルからしばしばファイルを生成する場合:

-   ディレクティブ プロセッサを記述することを検討します。 これにより、アセンブリの複数のステートメントを置換して、単一のカスタム ディレクティブを持つ各テンプレート内でステートメントをインポートすることができます。 ディレクティブ プロセッサはモデル ファイルを読み込み、解析できます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)

### <a name="generate-files-from-a-complex-model"></a>複雑なモデルからファイルを生成する

-   ドメイン固有言語 (DSL) を表すモデルを作成することを検討してください。 これによって、モデル内の要素の名前を反映した型とプロパティを使用するため、テンプレートの記述が簡単になります。 ファイルを解析したり、XML ノードを巡回したりする必要はありません。 例:

     `foreach (Book book in this.Library) { ... }`

     詳細については、次を参照してください。[ドメイン固有言語の概要](../modeling/getting-started-with-domain-specific-languages.md)と[ドメイン固有言語からコードを生成する](../modeling/generating-code-from-a-domain-specific-language.md)

### <a name="get-data-from-visual-studio"></a>Visual Studio からのデータの取得
 Visual Studio で提供されるサービスを使用するには、`hostSpecific` 属性を設定し、`EnvDTE` アセンブリをロードします。 例:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>ビルド プロセスでのテキスト テンプレートの実行

-   詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md) 

## <a name="more-general-questions"></a>一般的な質問

### <a name="starting"></a>テキスト テンプレートの作成を開始する最善の方法は何ですか?

1.  生成されたファイルの具体的な例を記述します。

2.  `<#@template #>` ディレクティブを挿入することで、テキスト テンプレートに変えます。ディレクティブとコードは、入力ファイルまたはモデルを読み込むために必要です。

3.  段階的に、ファイルの一部を式とコード ブロックに置き換えます。

### <a name="what-is-a-model"></a>「モデル」とは何ですか?

-   テンプレートによって読み取られる入力です。 ファイルまたはデータベースが考えられます。 XML、Visio 図面、ドメイン固有言語 (DSL)、UML モデルのいずれか、またはプレーン テキストである可能性があります。 これは、いくつかのファイルにまたがることがあります。 通常は、複数のテンプレートが、1 つのモデルを読み取ります。

     「モデル」という用語の意味は、プログラム コードやその他のファイルの生成というよりも、ビジネスの側面をより直接的に表現しています。 たとえば、生成されたソフトウェアが監督する通信ネットワークの計画を表しているかもしれません。

### <a name="what-is-the-benefit-of-using-text-templates"></a>テキスト テンプレートを使用する利点は何ですか?
 通常、1 つのモデルから複数のコードやその他のファイルを生成します。 モデルは、生成されるコードよりも直接的に要件を表しています。 実装の詳細を省略し、コードではなく、要件の観点から記述されます。 （あなたにもよくある）要件変更のとき、モデルの更新は、プログラム コードのさまざまな部分の更新よりも、より簡単かつより確実にできます。

 すなわち、コード生成は、アジャイル開発手法の観点から貴重なツールです。

### <a name="what-best-practices-are-there-for-text-templates"></a>テキスト テンプレートには、どのような「ベスト プラクティス」がありますか?

-   詳細については、次を参照してください。 [T4 テキスト テンプレートの記述に関するガイドライン](../modeling/guidelines-for-writing-t4-text-templates.md)

### <a name="what-is-t4"></a>"T4"とは何ですか?

-   ここで説明されている Visual Studio のテキスト テンプレート機能の別の名前です。 公開されていない以前のバージョンでは、「Text Template Transformation」の省略形でした。
