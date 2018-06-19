---
title: テキスト テンプレートから Visual Studio またはその他のホストへのアクセス
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 657abba976e0f0d167651943289296d340981e62
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946518"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>テキスト テンプレートから Visual Studio またはその他のホストにアクセスします。

テキスト テンプレートでは、メソッドとテンプレートを実行するホストによって公開されているプロパティを使用できます。 Visual Studio では、ホストの例を示します。

> [!NOTE]
> はなく、通常のテキスト テンプレートに、ホストのメソッドとプロパティを使用することができます*プリプロセス*テキスト テンプレートです。

## <a name="obtain-access-to-the-host"></a>ホストへのアクセスを取得します。

ホストにアクセスするには、設定`hostspecific="true"`で、`template`ディレクティブです。 使用して`this.Host`、型を持つ<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>します。 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>型が使用できる、たとえば、ファイル名を解決して、エラーをログするメンバー。

### <a name="resolve-file-names"></a>ファイル名を解決するには

テキスト テンプレートに関連するファイルの完全なパスを検索する`this.Host.ResolvePath()`です。

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>エラー メッセージを表示します。

この例は、テンプレートを変換するときにメッセージを記録します。 ホストが Visual Studio の場合は、エラーされるため、**エラー一覧**です。

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Visual Studio API を使用します。

使用することができますが、テキスト テンプレートは、Visual Studio で実行している場合、`this.Host`サービスにアクセスする Visual Studio と任意のパッケージまたは読み込まれている拡張機能によって提供されます。

設定 hostspecific ="true"とキャスト`this.Host`に<xref:System.IServiceProvider>です。

この例では Visual Studio API を取得<xref:EnvDTE.DTE>、サービスとして。

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>テンプレートの継承を持つ hostSpecific を使用します。

指定`hostspecific="trueFromBase"`使用する場合は、`inherits`属性を指定したテンプレートから継承する場合と`hostspecific="true"`です。 ない場合は、する可能性があります、コンパイラの警告をプロパティ`Host`は 2 回宣言されています。