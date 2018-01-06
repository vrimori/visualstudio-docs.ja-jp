---
title: "テキスト テンプレートを使用する方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: "11"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 351b9025ba4631a515f1f6cf627e27e6afb3cc88
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to--with-text-templates"></a>方法: テキスト テンプレートを使用する
テキスト テンプレートで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]任意の種類のテキストを生成する便利な方法を提供します。 テキスト テンプレートを使用すると、実行時に、アプリケーションの一部として、プロジェクト コードの一部を生成するのにデザイン時にテキストを生成します。 このトピックの内容をまとめたもの、最も頻繁に寄せられる「操作方法...」 問題があります。  
  
 このトピックでは、行頭に付けた複数の回答は、代替案の候補です。  
  
 テキスト テンプレートに一般的な概要については、読み取り[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)です。  
  
## <a name="how-to-"></a>操作方法。。。  
  
### <a name="generate-part-of-my-application-code"></a>アプリケーション コードの一部を生成します。  
 構成があるか、*モデル*ファイルまたはデータベースにします。 マイ コードの 1 つまたは複数の部分は、そのモデルによって異なります。  
  
-   テキスト テンプレートから、一部のコード ファイルを生成します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して、デザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)と[テンプレートの作成を開始する最善の方法は何ですか?](#starting)です。  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>テンプレートにデータを渡して、実行時にファイルを生成します。  
 、実行時に、アプリケーションは、標準のテキストとデータの組み合わせを含む、レポートなどのテキスト ファイルを生成します。 何百もが書き込まれないようにしたい`write`ステートメントです。  
  
-   実行時テキスト テンプレートをプロジェクトに追加します。 このテンプレートは、コードでインスタンスを作成および使用してテキストを生成することができるクラスを作成します。 コンス トラクターのパラメーターでにデータを渡すことができます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)です。  
  
-   実行時にのみ使用可能なテンプレートから生成する場合は、標準のテキスト テンプレートを使用できます。 作成している場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能では、テキスト テンプレート サービスを呼び出すことができます。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)です。 他のコンテキストでは、テキスト テンプレート エンジンを使用できます。 詳細については、「<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>」を参照してください。  
  
     使用して、 \<#@parameter#> ディレクティブにこれらのテンプレート パラメーターを渡します。 詳細については、次を参照してください。 [T4 パラメーター ディレクティブ](../modeling/t4-parameter-directive.md)です。  
  
### <a name="read-another-project-file-from-a-template"></a>テンプレートから別のプロジェクト ファイルを読み取り  
 同じファイルの読み取りに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト テンプレートとして。  
  
-   `hostSpecific="true"` ディレクティブに `<#@template#>` を挿入します。  
  
     コードを使用して`this.Host.ResolvePath(filename)`ファイルの完全パスを取得します。  
  
### <a name="invoke-methods-from-a-template"></a>テンプレートからメソッドを呼び出す  
 メソッドに存在しない場合、たとえば、標準[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]クラス。  
  
-   使用して、 \<#@assembly#> ディレクティブをアセンブリの読み込みし、使用\<#@import#> 名前空間コンテキストを設定します。 詳細については、次を参照してください。 [T4 インポート ディレクティブ](../modeling/t4-import-directive.md)です。  
  
     頻繁に同じアセンブリのセットを使用するディレクティブをインポートすると、ディレクティブ プロセッサの記述を検討してください。 各テンプレートでは、アセンブリとモデル ファイルの読み込みし、名前空間コンテキストを設定することができますが、ディレクティブ プロセッサを呼び出すことができます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)です。  
  
 作成する場合、メソッド自分で。  
  
-   実行時テキスト テンプレートを作成している場合は、実行時テキスト テンプレートと同じ名前のある部分クラス定義を作成します。 このクラスに追加のメソッドを追加します。  
  
-   クラス機能コントロール ブロックを書き込む`<#+ ... #>`になることができますを宣言するメソッド、プロパティ、およびプライベート クラスです。 テキスト テンプレートのコンパイル時に、クラスに変換されます。 標準コントロール ブロック`<#...#>`とテキストが変換されて 1 つのメソッド、およびクラス機能ブロックは個別のメンバーとして挿入されます。 詳細については、次を参照してください。[テキスト テンプレートのコントロール ブロック](../modeling/text-template-control-blocks.md)です。  
  
     クラスの機能では、埋め込みのテキスト ブロックを含めることも、定義されているメソッド。  
  
     クラスの機能をすることができますが、別のファイルに置くことを検討`<#@include#>`を 1 つまたは複数のテンプレート ファイルにします。  
  
-   別のアセンブリ (クラス ライブラリ) に、メソッドを記述し、テンプレートからこれらを呼び出します。 使用して、`<#@assembly#>`ディレクティブをアセンブリの読み込みと`<#@import#>`名前空間コンテキストを設定します。 注でデバッグするときに、アセンブリを再構築、するためにする場合もあることを停止して再起動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 詳細については、次を参照してください。 [T4 テキスト テンプレート ディレクティブ](../modeling/t4-text-template-directives.md)です。  
  
### <a name="generate-many-files-from-one-model-schema"></a>1 つのモデル スキーマから多数のファイルを生成します。  
 多くの場合、ファイルを生成するには、同じ XML フォーマット ファイルまたはデータベースのスキーマを持つモデルから: 場合  
  
-   ディレクティブ プロセッサの作成を検討します。 これにより、アセンブリの複数のステートメントを置換し、1 つのカスタム ディレクティブでは、各テンプレート内のステートメントをインポートすることができます。 ディレクティブ プロセッサは読み込むし、モデル ファイルを解析できます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)です。  
  
### <a name="generate-files-from-a-complex-model"></a>複雑なモデルからファイルを生成します。  
  
-   ドメイン固有言語 (DSL) を表す、モデルを作成することを検討します。 これはより簡単、テンプレートを記述する型と、モデル内の要素の名前を反映するプロパティを使用するためです。 ファイルを解析するか、XML ノード間を移動する必要はありません。 例:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     詳細については、次を参照してください。[ドメイン固有言語の使用を開始する](../modeling/getting-started-with-domain-specific-languages.md)と[ドメイン固有言語から、コードの生成](../modeling/generating-code-from-a-domain-specific-language.md)です。  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>データを取得します。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 提供されるサービスを使用する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、セットで、`hostSpecific`属性と負荷、`EnvDTE`アセンブリ。 例:  
  
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
  
-   詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)です。  
  
## <a name="more-general-questions"></a>一般的な質問  
  
###  <a name="starting"></a>テキスト テンプレートの作成を開始する最善の方法とは何ですか。  
  
1.  生成されたファイルの具体的な例を記述します。  
  
2.  挿入することで、テキスト テンプレートを変換すること、`<#@template #>`ディレクティブおよびディレクティブとコードを入力ファイルまたはモデルを読み込むために必要なです。  
  
3.  式とコード ブロックで、ファイルの部分が徐々 に置き換えます。  
  
### <a name="what-is-a-model"></a>「モデル」とは何ですか。  
  
-   テンプレートによって読み取られた入力します。 ファイルまたはデータベースがある可能性があります。 XML、または Visio 図面やドメイン固有言語 (DSL) または UML モデル、またはプレーン テキストがある可能性があります。 これは、いくつかのファイルに分散可能性があります。 通常 1 つ以上のテンプレートは、1 つのモデルを読み取ります。  
  
     用語「モデル」の意味は、ビジネスを生成するプログラム コードやその他のファイルよりも、直接の一部の側面を表すです。 たとえば、生成されるソフトウェアを管理する通信ネットワークの計画を表すことができます。  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>テキスト テンプレートを使用する利点は何ですか。  
 通常、1 つのモデルから複数のコードまたはその他のファイルを生成します。 モデルでは、生成されたコードよりも直接の要件を表します。 実装の詳細を省略して、コードではなく、要件の観点から書き込まれます。 要件の変更 - のように通常の場合より簡単かつより、プログラム コードの異なる部分も確実にモデルを更新できます。  
  
 コードの生成は、アジャイル開発方法の観点から重要なツールではこのためです。  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>どのような「ベスト プラクティス」は、テキスト テンプレートにはありますか。  
  
-   詳細については、次を参照してください。 [T4 テキスト テンプレートの記述に関するガイドライン](../modeling/guidelines-for-writing-t4-text-templates.md)です。  
  
### <a name="what-is-t4"></a>"T4"とは何ですか。  
  
-   別の名前、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレートの機能がここで説明します。 パブリッシュされておらず、以前のバージョンでは、「テキスト テンプレート変換」の省略形はでした。
