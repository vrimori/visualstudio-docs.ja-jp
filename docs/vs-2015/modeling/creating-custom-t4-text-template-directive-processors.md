---
title: カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d4e0b6b325f2418c031f00defc0f28bd2fc6b3f0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176931"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*テキスト テンプレート変換プロセス*は、*テキスト テンプレート*ファイルとして入力し、テキスト ファイルを出力として生成します。 *テキスト テンプレート変換エンジン*コントロール、プロセスと、エンジンは、テキスト テンプレート変換ホストおよび 1 つまたは複数のテキスト テンプレートと対話する*ディレクティブ プロセッサ*を完了する、プロセスです。 詳細については、次を参照してください。 [、テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)します。  
  
 カスタム ディレクティブ プロセッサを作成するには、<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> または <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> を継承するクラスを作成します。  
  
 これらの 2 つの違いは<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>ユーザーからパラメーターを取得し、テンプレートの出力ファイルを生成するコードを生成するために必要な最小のインターフェイスを実装します。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 実装して、必要がありますは設計パターン。 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 2 つの特別なパラメーターを処理する`requires`と`provides`します。  たとえば、カスタム ディレクティブ プロセッサ可能性がありますから、ユーザーは、開いているファイル名をそのまま使用ファイルを読み取るし、という名前の変数で、ファイルのテキストを格納`fileText`します。 サブクラスの<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>クラスの値として、ユーザーからファイル名を取得する可能性があります、`requires`パラメーター、およびの値として、テキストを格納する変数の名前、`provides`パラメーター。 このプロセッサは開きとファイルの読み取り、指定された変数で、ファイルのテキストを格納します。  
  
 テキスト テンプレートからカスタム ディレクティブ プロセッサを呼び出す前に[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、登録する必要があります。  
  
 レジストリ キーを追加する方法の詳細については、次を参照してください。[カスタム ディレクティブ プロセッサの配置](../modeling/deploying-a-custom-directive-processor.md)します。  
  
## <a name="custom-directives"></a>カスタム ディレクティブ  
 カスタム ディレクティブのようになります。  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 テキスト テンプレートから外部データまたはリソースにアクセスする場合は、カスタム ディレクティブ プロセッサを使用できます。  
  
 ディレクティブ プロセッサが再利用するためのコードを分解する方法を提供するため、別のテキスト テンプレートでは、1 つのディレクティブ プロセッサが提供する機能を共有できます。 組み込み`include`ディレクティブは、使用してコードを取り除くし、別のテキスト テンプレート間で共有するためも同様です。 違いは任意の機能を`include`は固定され、パラメーターを受け入れませんディレクティブを提供します。 テキスト テンプレートに共通の機能を提供し、テンプレート パラメーターを渡す場合は、カスタム ディレクティブ プロセッサを作成する必要があります。  
  
 カスタム ディレクティブ プロセッサの例をいくつか考えられます。  
  
-   ユーザー名とパスワードをパラメーターとして受け取るデータベースからデータを返すディレクティブ プロセッサ。  
  
-   開いて、ファイルを読み取るディレクティブ プロセッサは、パラメーターとして、ファイルの名前を受け取ります。  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>カスタム ディレクティブ プロセッサの主要な要素  
 ディレクティブ プロセッサを開発するには、いずれかから継承するクラスを作成する必要があります<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>または<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>します。  
  
 最も重要な`DirectiveProcessor`を実装する必要があるメソッドは、次のとおりです。  
  
-   `bool IsDirectiveSupported(string directiveName)` -戻り`true`ディレクティブ プロセッサは、名前付きディレクティブを扱うことができる場合。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -テンプレート エンジンでは、テンプレートのディレクティブの各インスタンスに対してこのメソッドを呼び出します。 プロセッサは、結果を保存する必要があります。  
  
 ProcessDirective() に対するすべての呼び出し後に、テンプレート エンジンはこれらのメソッドを呼び出します。  
  
-   `string[] GetReferencesForProcessingRun()` -テンプレート コードを必要とするアセンブリの名前を返します。  
  
-   `string[] GetImportsForProcessingRun()` -テンプレート コードで使用できる名前空間を返します。  
  
-   `string GetClassCodeForProcessingRun()` -メソッド、プロパティ、およびテンプレート コードで使用できるその他の宣言のコードを返します。 これを行う最も簡単な方法では、c# または Visual Basic コードを含む文字列を作成します。 ディレクティブ プロセッサを任意の CLR 言語を使用するテンプレートから呼び出すことができるように、CodeDom ツリーとして、ステートメントを作成し、テンプレートで使用する言語でツリーをシリアル化の結果を返すできます。  
  
-   詳細については、次を参照してください。[チュートリアル: カスタム ディレクティブ プロセッサの作成](../modeling/walkthrough-creating-a-custom-directive-processor.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [カスタム ディレクティブ プロセッサの配置](../modeling/deploying-a-custom-directive-processor.md)  
 カスタム ディレクティブ プロセッサを登録する方法について説明します。  
  
 [チュートリアル: カスタム ディレクティブ プロセッサの作成](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 カスタム ディレクティブ プロセッサを作成する方法、登録およびディレクティブ プロセッサをテストする方法と、出力ファイルを HTML として書式設定する方法について説明します。



