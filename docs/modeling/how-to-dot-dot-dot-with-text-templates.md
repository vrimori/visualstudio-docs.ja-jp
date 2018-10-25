---
title: '方法: テキスト テンプレートを使用する'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20dbc5223ddb053355fa5e8076ae66badee688a4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883075"
---
# <a name="how-to--with-text-templates"></a>方法: テキスト テンプレートを使用する
Visual Studio でテキスト テンプレートでは、あらゆる種類のテキストを生成するのに便利な方法を提供します。 テキスト テンプレートを使用すると、実行時に、アプリケーションの一部として、デザイン時、プロジェクト コードの一部を生成するのにテキストを生成します。 このトピックでは、最も頻繁にまとめたものです"How do I..."よく寄せられる 質問します。

 このトピックでは、行頭文字が付いている複数の回答は別の提案です。

 テキスト テンプレートに一般的な概要については、読み取る[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。

## <a name="how-to-"></a>操作方法 ...

### <a name="generate-part-of-my-application-code"></a>アプリケーション コードの一部を生成します。
 構成があるまたは*モデル*ファイルまたはデータベースにします。 マイ コードの 1 つまたは複数の部分は、そのモデルに依存します。

-   テキスト テンプレートからは、一部のコード ファイルを生成します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)と[テンプレートの作成を開始する最善の方法は何ですか?](#starting)します。

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>テンプレートにデータを渡して、実行時にファイルを生成します。
 実行時に、アプリケーションは、標準のテキストとデータの組み合わせを含むレポートなどのテキスト ファイルを生成します。 何百もの書き込みを回避したい`write`ステートメント。

-   ランタイム テキスト テンプレートをプロジェクトに追加します。 このテンプレートでは、インスタンス化し、使用してテキストを生成することができるコードでクラスを作成します。 データは、コンス トラクターのパラメーターを渡すことができます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)します。

-   実行時にのみ使用可能なテンプレートから生成する場合は、標準のテキスト テンプレートを使用できます。 Visual Studio 拡張機能を作成する場合は、テキスト テンプレート サービスを呼び出すことができます。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。 他のコンテキストで、テキスト テンプレート エンジンを使用することができます。 詳細については、「 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 」を参照してください。

     使用して、 \<#@parameter#> ディレクティブには、これらのテンプレート パラメーターを渡します。 詳細については、次を参照してください。 [T4 パラメーター ディレクティブ](../modeling/t4-parameter-directive.md)します。

### <a name="read-another-project-file-from-a-template"></a>テンプレートから別のプロジェクト ファイルを読み取る
 テンプレートと同じ Visual Studio プロジェクトからファイルの読み取り。

-   `hostSpecific="true"` ディレクティブに `<#@template#>` を挿入します。

     コードで、次のように使用します。`this.Host.ResolvePath(filename)`ファイルの完全なパスを取得します。

### <a name="invoke-methods-from-a-template"></a>テンプレートからメソッドを呼び出し
 メソッド、既に存在する場合など、標準で[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]クラス。

- 使用して、 \<#@assembly#> ディレクティブは、アセンブリをロードして使用する\<#@import#> 名前空間のコンテキストを設定します。 詳細については、次を参照してください。 [T4 インポート ディレクティブ](../modeling/t4-import-directive.md)します。

   頻繁に同じアセンブリのセットを使用して、ディレクティブをインポートすると、ディレクティブ プロセッサの作成を検討してください。 各テンプレートでは、アセンブリとモデル ファイルを読み込むし、名前空間のコンテキストを設定できますが、ディレクティブ プロセッサを呼び出すことができます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)です。

  場合は、メソッドは、自分で作成しています。

- ランタイム テキスト テンプレートを作成する場合、ランタイム テキスト テンプレートと同じ名前を持つ部分クラス定義を記述します。 このクラスに、追加のメソッドを追加します。

- クラス機能コントロール ブロックを書き込む`<#+ ... #>`でメソッド、プロパティ、およびプライベートのクラス宣言できますが。 テキスト テンプレートのコンパイル時に、クラスに変換されます。 標準コントロール ブロック`<#...#>`テキストが 1 つのメソッドに変換され、別のメンバーとしてクラス機能ブロックが挿入されます。 詳細については、次を参照してください。[テキスト テンプレートのコントロール ブロック](../modeling/text-template-control-blocks.md)します。

   メソッドはクラスの機能は、埋め込みのテキスト ブロックを含めることができますもとして定義します。

   可能な別のファイルにクラスの機能を配置すること検討`<#@include#>`を 1 つまたは複数のテンプレート ファイルにします。

- 別のアセンブリ (クラス ライブラリ) で、メソッドを記述し、テンプレートから呼び出すことです。 使用して、`<#@assembly#>`ディレクティブは、アセンブリの読み込みと`<#@import#>`名前空間のコンテキストを設定します。 それをデバッグするときに、アセンブリを再構築するためにする必要がありますを停止し、Visual Studio を再起動に注意してください。 詳細については、次を参照してください。 [T4 テキスト テンプレート ディレクティブ](../modeling/t4-text-template-directives.md)します。

### <a name="generate-many-files-from-one-model-schema"></a>1 つのモデル スキーマから多数のファイルを生成します。
 多くの場合、ファイルを生成するには、同じ XML またはデータベース スキーマを持つモデルから: 場合

-   ディレクティブ プロセッサを書き込むことを検討します。 これにより、アセンブリの複数のステートメントを置換して、1 つのカスタム ディレクティブでは、各テンプレート内のステートメントをインポートすることができます。 ディレクティブ プロセッサは読み込みし、モデル ファイルを解析できます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)です。

### <a name="generate-files-from-a-complex-model"></a>複雑なモデルからファイルを生成します。

-   ドメイン固有言語 (DSL) を表すモデルを作成することを検討してください。 これによって、テンプレートの記述が簡単型と、モデル内の要素の名前を反映するプロパティを使用するためです。 ファイルを解析するか、XML ノードを移動する必要はありません。 例えば:

     `foreach (Book book in this.Library) { ... }`

     詳細については、次を参照してください。[ドメイン固有言語の概要](../modeling/getting-started-with-domain-specific-languages.md)と[ドメイン固有言語からコードを生成する](../modeling/generating-code-from-a-domain-specific-language.md)します。

### <a name="get-data-from-visual-studio"></a>Visual Studio からのデータを取得します。
 Visual Studio で、セットによって提供されるサービスを使用する、`hostSpecific`属性と負荷、`EnvDTE`アセンブリ。 例えば:

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

### <a name="execute-text-templates-in-the-build-process"></a>ビルド プロセスでテキスト テンプレートを実行します。

-   詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)します。

## <a name="more-general-questions"></a>一般的な質問

### <a name="starting"></a> テキスト テンプレートの作成を開始する最善の方法とは何ですか。

1.  生成されたファイルの具体的な例を記述します。

2.  挿入することで、テキスト テンプレートに変えます、`<#@template #>`ディレクティブおよびディレクティブとコードを入力ファイルまたはモデルを読み込むために必要な。

3.  段階的に式とコード ブロックで、ファイルの部分を置き換えます。

### <a name="what-is-a-model"></a>「モデル」とは何ですか。

-   テンプレートによって読み取られた入力します。 ファイルまたはデータベースが考えられます。 XML、または Visio 図面では、またはドメイン固有言語 (DSL)、または UML モデル、またはプレーン テキストである可能性があります。 これは、いくつかのファイルの間で分散でした。 通常は、複数のテンプレートは、1 つのモデルを読み取ります。

     「モデル」という用語の意味は、ビジネスを生成するプログラム コードやその他のファイルよりも、直接の一部の側面を表現しています。 たとえば、通信ネットワーク、生成されるソフトウェアが監督のプランを表すこともできます。

### <a name="what-is-the-benefit-of-using-text-templates"></a>テキスト テンプレートを使用する利点は何ですか。
 通常、1 つのモデルから複数のコードやその他のファイルを生成します。 モデルでは、生成されたコードよりも直接要件を表します。 実装の詳細を省略して、コードではなく、要件の観点から書き込まれます。 要件の変更 - のように、通常のときにより簡単かつプログラム コードの別の部分よりも確実にモデルを更新できます。

 コード生成は、そのため、アジャイル開発手法の観点からの貴重なツールです。

### <a name="what-best-practices-are-there-for-text-templates"></a>どのような「ベスト プラクティス」のテキスト テンプレートではありますか。

-   詳細については、次を参照してください。 [T4 テキスト テンプレートの記述に関するガイドライン](../modeling/guidelines-for-writing-t4-text-templates.md)します。

### <a name="what-is-t4"></a>"T4"とは何ですか。

-   ここで説明されている Visual Studio のテキスト テンプレート機能に別の名前。 以前のバージョンは発行されませんでしたが、「テキスト テンプレート変換」の省略形。
