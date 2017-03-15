---
title: "カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, カスタム ディレクティブ プロセッサ"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*テキスト テンプレート変換プロセス*では、*テキスト テンプレート* ファイルを入力として受け取り、テキスト ファイルを出力として生成します。  このプロセスは、*テキスト テンプレート変換エンジン*によって制御されます。テキスト テンプレート変換エンジンが、テキスト テンプレート変換ホストおよび 1 つまたは複数のテキスト テンプレート *ディレクティブ プロセッサ*と対話しながら、このプロセスを実行します。  詳細については、「[テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)」を参照してください。  
  
 カスタム ディレクティブ プロセッサを作成するには、<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> または <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> を継承するクラスを作成します。  
  
 これらの 2 つの違いは、<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> には、ユーザーからパラメーターを取得し、テンプレート出力ファイルを作成するコードを生成するために必要な最低限のインターフェイスしか実装されていない点にあります。  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> には、requires\/provides デザイン パターンが実装されています。  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> は、`requires` と `provides` という 2 つの特殊なパラメーターを処理します。  たとえば、ユーザーからファイル名を受け取り、そのファイルを開いて読み取った後、`fileText` という名前の変数にファイルのテキストを格納するカスタム ディレクティブ プロセッサがあるとします。  この場合、<xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> クラスのサブクラスは、ファイル名とテキストを格納するための変数の名前とを、それぞれ `requires` パラメーターおよび `provides` パラメーターの値としてユーザーから受け取ることになります。  すると、このプロセッサが、ファイルを開いて読み取った後、指定された変数にそのファイルのテキストを格納します。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でテキスト テンプレートからカスタム ディレクティブ プロセッサを呼び出すには、あらかじめそれを登録しておく必要があります。  
  
 レジストリ キーを追加する方法の詳細については、「[カスタム ディレクティブ プロセッサの配置](../modeling/deploying-a-custom-directive-processor.md)」を参照してください。  
  
## カスタム ディレクティブ  
 カスタム ディレクティブは、次のように記述されます。  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 カスタム ディレクティブ プロセッサを使用すると、テキスト テンプレートから外部のデータまたはリソースにアクセスすることができます。  
  
 1 つのディレクティブ プロセッサが備えている機能を複数のテキスト テンプレートで共有できるという点で、ディレクティブ プロセッサには、コードを分解して再利用できるようにする働きがあります。  コードの一部を取り出して、複数のテキスト テンプレート間で共有できるという点では、組み込みの `include` ディレクティブと似ています。  両者の違いは、`include` ディレクティブが備えている機能はすべて固定的であり、パラメーターを受け取らないことです。  共通の機能をテキスト テンプレートに提供し、テンプレートからパラメーターを渡すことができるようにするには、カスタム ディレクティブ プロセッサを作成する必要があります。  
  
 以下に、カスタム ディレクティブ プロセッサの使用例をいくつか紹介します。  
  
-   データベースからデータを取得するディレクティブ プロセッサ。ユーザー名とパスワードをパラメーターとして受け取ります。  
  
-   ファイルを開いて読み取るディレクティブ プロセッサ。パラメーターとしてファイル名を受け取ります。  
  
### カスタム ディレクティブ プロセッサの主要な要素  
 ディレクティブ プロセッサを開発するには、<xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> または <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> を継承するクラスを作成する必要があります。  
  
 `DirectiveProcessor` のメソッドのうち、実装する必要のある最も重要なメソッドは次のとおりです。  
  
-   `bool IsDirectiveSupported(string directiveName)`: ディレクティブ プロセッサが名前付きのディレクティブを扱うことができる場合に `true` を返します。  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`: テンプレート内の各ディレクティブについて、このメソッドがテンプレート エンジンによって呼び出されます。  カスタム プロセッサはその結果を保存する必要があります。  
  
 ProcessDirective\(\) の呼び出しがすべて完了した後、テンプレート エンジンによって次のメソッドが呼び出されます。  
  
-   `string[] GetReferencesForProcessingRun()`: テンプレート コードに必要なアセンブリの名前を返します。  
  
-   `string[] GetImportsForProcessingRun()`: テンプレート コードで使用できる名前空間を返します。  
  
-   `string GetClassCodeForProcessingRun()`: テンプレート コードから使用できるメソッド、プロパティ、およびその他の宣言のコードを返します。  これを行う最も簡単な方法は、C\# または Visual Basic コードを格納する文字列を構築することです。  CLR 言語を使用したテンプレートからカスタム ディレクティブ プロセッサを呼び出すことができるようにするには、ステートメントを CodeDom ツリーとして構築し、そのツリーをテンプレートの使用言語でシリアル化した結果を返します。  
  
-   詳細については、「[チュートリアル: カスタム ディレクティブ プロセッサの作成](../modeling/walkthrough-creating-a-custom-directive-processor.md)」を参照してください。  
  
## このセクションの内容  
 [カスタム ディレクティブ プロセッサの配置](../modeling/deploying-a-custom-directive-processor.md)  
 カスタム ディレクティブ プロセッサの登録方法について説明します。  
  
 [チュートリアル: カスタム ディレクティブ プロセッサの作成](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 カスタム ディレクティブ プロセッサの作成方法、ディレクティブ プロセッサを登録してテストする方法、および、出力ファイルを HTML として書式設定する方法を説明します。