---
title: "カスタム T4 テキスト テンプレート ディレクティブ プロセッサを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e220692b263dbb35779c25ff0b189f219e98b842
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成
*テキスト テンプレート変換プロセス*受け取り、*テキスト テンプレート*ファイルとして入力し、テキスト ファイルを出力として生成します。 *テキスト テンプレート変換エンジン*コントロール、プロセスと、エンジンは、テキスト テンプレート変換ホストおよび 1 つまたは複数のテキスト テンプレートと対話する*ディレクティブ プロセッサ*プロセスを完了します。 詳細については、次を参照してください。 [、テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)です。  
  
 カスタム ディレクティブ プロセッサを作成するには、<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> または <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> を継承するクラスを作成します。  
  
 これらの 2 つの違いを<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>ユーザーからパラメーターを取得して、テンプレート出力ファイルを生成するコードを生成するために必要な最小のインターフェイスを実装します。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>実装して、デザイン パターンを必要と/提供します。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>2 つの特殊なパラメーターを処理する`requires`と`provides`です。  たとえば、カスタム ディレクティブ プロセッサ可能性がありますから、ユーザーは、開いているファイル名を受け取るファイルを読み取るし、という名前の変数に、ファイルのテキストを格納`fileText`です。 サブクラス、<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>クラスの値として、ユーザーからファイル名を取得する可能性があります、`requires`パラメーター、およびの値として、テキストを格納する変数の名前、`provides`パラメーター。 このプロセッサはおよびファイルの読み取りを開き、指定した変数に、ファイルのテキストを格納します。  
  
 内のテキスト テンプレートから、カスタム ディレクティブ プロセッサを呼び出す前に[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、登録する必要があります。  
  
 レジストリ キーを追加する方法の詳細については、次を参照してください。[カスタム ディレクティブ プロセッサの配置](../modeling/deploying-a-custom-directive-processor.md)です。  
  
## <a name="custom-directives"></a>カスタム ディレクティブ  
 カスタム ディレクティブは、このようになります。  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`  
  
 テキスト テンプレートから外部データやリソースにアクセスするときに、カスタム ディレクティブ プロセッサを使用することができます。  
  
 複数のテキスト テンプレートは、ので、再利用するためのコードを分解する方法を指定するディレクティブ プロセッサ、1 つのディレクティブ プロセッサが提供する機能を共有できます。 組み込み`include`ディレクティブと同様に、使用してコードを分解して、複数のテキスト テンプレート間で共有するためです。 違いは、の機能をすべてを`include`ディレクティブの提供は固定され、パラメーターを使用しません。 テキスト テンプレートに共通の機能を提供し、テンプレート パラメーターを渡すを許可する場合は、カスタム ディレクティブ プロセッサを作成する必要があります。  
  
 カスタム ディレクティブ プロセッサの例をいくつかが考えられます。  
  
-   ディレクティブ プロセッサをパラメーターとしてユーザー名とパスワードを受け取るデータベースからデータを取得します。  
  
-   開き、ファイルを読み取るディレクティブ プロセッサは、パラメーターとして、ファイルの名前を受け入れます。  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>カスタム ディレクティブ プロセッサの主要な要素  
 ディレクティブ プロセッサを開発するには、いずれかから継承するクラスを作成する必要があります<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>または<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>です。  
  
 最も重要な`DirectiveProcessor`を実装する必要があるメソッドは次のとおりです。  
  
-   `bool IsDirectiveSupported(string directiveName)`-戻り`true`場合は、ディレクティブ プロセッサは、名前付きのディレクティブを扱うことができます。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`-テンプレート エンジンでは、テンプレートのディレクティブの発生するたびにこのメソッドを呼び出します。 プロセッサは、結果を保存する必要があります。  
  
 ProcessDirective() に対するすべての呼び出し後に、テンプレート エンジンはこれらのメソッドを呼び出します。  
  
-   `string[] GetReferencesForProcessingRun()`-テンプレート コードを必要とするアセンブリの名前を返します。  
  
-   `string[] GetImportsForProcessingRun()`-テンプレート コードで使用できる名前空間を返します。  
  
-   `string GetClassCodeForProcessingRun()`メソッド、プロパティ、およびテンプレート コードで使用できるその他の宣言のコードを返します。 これを行う最も簡単な方法では、c# または Visual Basic コードを含む文字列を作成します。 ディレクティブ プロセッサを任意の CLR 言語を使用するテンプレートから呼び出すことができるようにするには、CodeDom ツリーとしてステートメントを構築し、テンプレートで使用する言語で、ツリーのシリアル化の結果を返すできます。  
  
-   詳細については、次を参照してください。[チュートリアル: カスタム ディレクティブ プロセッサの作成](../modeling/walkthrough-creating-a-custom-directive-processor.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [カスタム ディレクティブ プロセッサの配置](../modeling/deploying-a-custom-directive-processor.md)  
 カスタム ディレクティブ プロセッサを登録する方法について説明します。  
  
 [チュートリアル: カスタム ディレクティブ プロセッサの作成](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 カスタム ディレクティブ プロセッサを作成する方法、登録して、ディレクティブ プロセッサをテストする方法、および出力ファイルを HTML として書式設定する方法について説明します。