---
title: テキスト テンプレートから Visual Studio またはその他のホストへのアクセス
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 4381393352665eee3fd4d0c45aa86f2e56a1cd61
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877255"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>テキスト テンプレートからの Visual Studio またはその他のホストへのアクセス

テキスト テンプレートでは、メソッドと、テンプレートを実行するホストによって公開されているプロパティを使用できます。 Visual Studio は、ホストの例のひとつです。

> [!NOTE]
> 通常のテキスト テンプレートで、ホストのメソッドとプロパティを使用することができますが、*前処理*テキスト テンプレートではできません。

## <a name="obtain-access-to-the-host"></a>ホストへのアクセスの取得

ホストにアクセスするには、`template`ディレクティブで、`hostspecific="true"`を設定します。 それにより、 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 型を持つ`this.Host` が使用できるようになります。 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 型は、たとえば、ファイル名の解決や、エラーをログするメンバーを持っており、使用できます。

### <a name="resolve-file-names"></a>ファイル名を解決するには

テキスト テンプレートからのファイルの相対パスから完全なパスを検索するには、`this.Host.ResolvePath()` を使います。

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

### <a name="display-error-messages"></a>エラー メッセージの表示

この例は、テンプレートを変換するときのメッセージを記録します。 ホストが Visual Studio の場合は、エラーは、**エラー一覧**に追加されます。

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

## <a name="use-the-visual-studio-api"></a>Visual Studio API の使用

テキスト テンプレートを、Visual Studio で実行している場合、 Visual Studio と任意のパッケージまたは読み込まれている拡張機能によって提供されるサービスにアクセスするために、`this.Host` を使用することができます。

`hostspecific ="true"` を設定し、`this.Host` を <xref:System.IServiceProvider> にキャストします。

この例では Visual Studio API である <xref:EnvDTE.DTE> をサービスとして取得します。

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

## <a name="use-hostspecific-with-template-inheritance"></a>テンプレートを継承をしている hostSpecific の使用

`inherits`属性を使用し、`hostspecific="true"` を指定したテンプレートから継承する場合は、`hostspecific="trueFromBase"` を指定します。指定しなかった場合は、プロパティ `Host` が 2 回宣言されているというコンパイラ警告が出るでしょう。
