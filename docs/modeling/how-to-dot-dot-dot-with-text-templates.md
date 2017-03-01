---
title: "テキスト テンプレートを使用する方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>方法: テキスト テンプレートを使用する
テキスト テンプレートで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]あらゆる種類のテキストを生成する便利な方法を提供します。 テキスト テンプレートを使用すると、実行時に、アプリケーションの一部として、いくつかのプロジェクト コードを生成するのにデザイン時にテキストを生成します。 ここで、最も頻繁に要求の"How do I..." 質問します。  
  
 このトピックでは、行頭文字で始めることが複数の回答は、代替案の候補です。  
  
 テキスト テンプレートに全般的な概要については、読み取り[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。  
  
## <a name="how-to-"></a>操作方法。。。  
  
### <a name="generate-part-of-my-application-code"></a>アプリケーション コードの一部を生成します。  
 構成があるか、*モデル*ファイルまたはデータベースにします。 コードの&1; つまたは複数の部分は、そのモデルによって異なります。  
  
-   テキスト テンプレートから、一部のコード ファイルを生成します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して、デザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)と[テンプレートの作成を開始する最適な方法は何ですか?](#starting)します。  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>テンプレートにデータを渡して、実行時にファイルを生成します。  
 実行時に、アプリケーションは、標準のテキストとデータの組み合わせを含むレポートなどのテキスト ファイルを生成します。 何百もが書き込まれないようにしたい`write`ステートメントです。  
  
-   実行時テキスト テンプレートをプロジェクトに追加します。 このテンプレートでは、インスタンス化して、テキストの生成に使用されるコードでクラスを作成します。 データは、コンス トラクターのパラメーターを渡すことができます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)します。  
  
-   実行時にのみ使用できるテンプレートから生成する場合は、標準的なテキスト テンプレートを使用することができます。 作成している場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能では、テキスト テンプレート サービスを呼び出すことができます。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出して](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。 他のコンテキストでは、テキスト テンプレート エンジンを使用することができます。 詳細については、 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>。</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>を参照してください。  
  
     使用して、 \<#@parameter#> これらのテンプレートにパラメーターを渡すディレクティブです。 詳細については、次を参照してください。 [T4 パラメーター ディレクティブ](../modeling/t4-parameter-directive.md)します。  
  
### <a name="read-another-project-file-from-a-template"></a>テンプレートから別のプロジェクト ファイルを読み取る  
 同じファイルの読み取りに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テンプレートとプロジェクト。  
  
-   `hostSpecific="true"` ディレクティブに `<#@template#>` を挿入します。  
  
     コードでは、次のように使用します。`this.Host.ResolvePath(filename)`ファイルの完全パスを取得します。  
  
### <a name="invoke-methods-from-a-template"></a>テンプレートからメソッドを呼び出す  
 メソッドに存在しない場合、たとえば、標準[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]クラス。  
  
-   使用して、 \<#@assembly#>、アセンブリをロードして使用するディレクティブ\<#@import#> 名前空間のコンテキストを設定します。 詳細については、次を参照してください。 [T4 インポート ディレクティブ](../modeling/t4-import-directive.md)します。  
  
     多くの場合、同じアセンブリのセットを使用してディレクティブをインポートすると、ディレクティブ プロセッサの作成を検討してください。 各テンプレートには、アセンブリとモデル ファイルをロードして、名前空間のコンテキストが設定される、ディレクティブ プロセッサを呼び出すことができます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)します。  
  
 作成する場合、メソッド自分で。  
  
-   実行時テキスト テンプレートを作成する場合は、実行時テキスト テンプレートと同じ名前を持つ部分クラス定義を記述します。 このクラスに追加のメソッドを追加します。  
  
-   クラス機能コントロール ブロックを書き込む`<#+ ... #>`することができますを宣言するメソッド、プロパティ、およびプライベート クラスにします。 テキスト テンプレートのコンパイル時に、クラスに変換されます。 標準コントロール ブロック`<#...#>`テキストが&1; つのメソッドに変換され、別のメンバーとしてクラス機能ブロックに挿入されます。 詳細については、次を参照してください。[テキスト テンプレートのコントロール ブロック](../modeling/text-template-control-blocks.md)します。  
  
     クラスの機能では、埋め込みのテキスト ブロックを含めることも、定義されているメソッド。  
  
     可能な別のファイルにクラスの機能を配置することを検討してください`<#@include#>`を&1; つまたは複数のテンプレート ファイルにします。  
  
-   別のアセンブリ (クラス ライブラリ) で、メソッドを記述し、テンプレートからこれらを呼び出します。 使用して、`<#@assembly#>`ディレクティブで使用するアセンブリを読み込むことと`<#@import#>`名前空間のコンテキストを設定します。 注、デバッグ中に、アセンブリを再構築するためにある可能性を停止して再開[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 詳細については、次を参照してください。 [T4 テキスト テンプレート ディレクティブ](../modeling/t4-text-template-directives.md)します。  
  
### <a name="generate-many-files-from-one-model-schema"></a>1 つのモデル スキーマから多数のファイルを生成します。  
 場合は、多くの場合、ファイルは、同じ XML またはデータベース スキーマを持つモデルから生成します。  
  
-   ディレクティブ プロセッサの作成を検討します。 これにより、アセンブリの複数のステートメントを置き換えるし、単一のカスタム ディレクティブでは、各テンプレート内のステートメントをインポートすることができます。 ディレクティブ プロセッサは読み込むし、モデル ファイルを解析できます。 詳細については、次を参照してください。[カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)します。  
  
### <a name="generate-files-from-a-complex-model"></a>複雑なモデルからファイルを生成します。  
  
-   ドメイン固有言語 (DSL) を表す、モデルを作成することを検討します。 これによってより簡単に、テンプレートを記述できる型と、モデル内の要素の名前を反映するプロパティを使用するためです。 このファイルを解析または XML ノード間を移動する必要はありません。 例:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     詳細については、次を参照してください。[ドメイン固有言語の概要](../modeling/getting-started-with-domain-specific-languages.md)と[ドメイン固有言語からコードを生成する](../modeling/generating-code-from-a-domain-specific-language.md)です。  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>データを取得します。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 提供されるサービスを使用する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、セットによって、`hostSpecific`属性と負荷、`EnvDTE`アセンブリ。 例:  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>ビルド プロセスでのテキスト テンプレートを実行します。  
  
-   詳細については、次を参照してください。[ビルド プロセスでのコード生成](../modeling/code-generation-in-a-build-process.md)します。  
  
## <a name="more-general-questions"></a>一般的な質問  
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>テキスト テンプレートの作成を開始する最善の方法は何ですか。  
  
1.  生成されたファイルの具体的な例を記述します。  
  
2.  挿入することで、テキスト テンプレートに変えます、`<#@template #>`ディレクティブおよびディレクティブとコードを入力ファイルまたはモデルを読み込むために必要なです。  
  
3.  式とコード ブロックを使って、ファイルの部分を段階的に交換してください。  
  
### <a name="what-is-a-model"></a>「モデル」とは何ですか。  
  
-   テンプレートを基に読み取った入力します。 ファイルまたはデータベースがある可能性があります。 XML、または Visio 図面やドメイン固有言語 (DSL)、または UML モデル、またはプレーン テキストがある可能性があります。 いくつかのファイル間で分散する可能性があります。 通常複数のテンプレートは、1 つのモデルを読み取ります。  
  
     「モデル」という用語の意味は、ビジネスを生成するプログラム コードまたはその他のファイルよりも、直接の一部の側面を表すことです。 たとえば、生成されるソフトウェアを管理する通信ネットワークの計画を表すことができます。  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>テキスト テンプレートを使用する利点は何ですか。  
 通常、1 つのモデルから複数のコードやその他のファイルを生成します。 モデルでは、生成されたコードよりも直接の要件を表します。 実装の細部を省略し、コードではなく、要件として書き込まれます。 ように通常 –、要件の変更時に、容易になり、プログラム コードのさまざまな部分よりも確実に、モデルを更新できます。  
  
 コード生成は、そのため、アジャイル開発手法の観点からの貴重なツールです。  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>どのような「ベスト プラクティス」のテキスト テンプレートではありますか。  
  
-   詳細については、次を参照してください。 [T4 テキスト テンプレートの作成に関するガイドライン](../modeling/guidelines-for-writing-t4-text-templates.md)します。  
  
### <a name="what-is-t4"></a>"T4"とは何ですか。  
  
-   別の名前、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレートの機能がここで説明します。 パブリッシュされておらず、以前のバージョンでは、「テキスト テンプレート変換」の略語をしました。

