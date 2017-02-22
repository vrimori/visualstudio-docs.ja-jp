---
title: "テキスト テンプレートから Visual Studio またはその他のホストへのアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
caps.handback.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# テキスト テンプレートから Visual Studio またはその他のホストへのアクセス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト テンプレートでは、テンプレートを実行するホスト \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] など\) によって公開されるメソッドとプロパティを使用できます。  
  
 これは、前処理されたテキスト テンプレートではなく、標準のテキスト テンプレートに当てはまります。  
  
## ホストへのアクセスの取得  
 `template` ディレクティブで `hostspecific="true"` を設定します。  これにより、<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> 型の `this.Host` を使用できるようになります。  この型は、ファイル名の解決やエラー ログの記録などに使用できるメンバーを持ちます。  
  
### ファイル名の解決  
 テキスト テンプレートに関連するファイルの完全パスを確認するには、this.Host.ResolvePath\(\) を使用します。  
  
```c#  
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
  
### エラー メッセージの表示  
 この例では、テンプレートの変換時にメッセージ ログを記録します。  ホストが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の場合は、エラー ウィンドウにメッセージ ログが追加されます。  
  
```c#  
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
  
## Visual Studio API の使用  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でテキスト テンプレートを実行する場合は、`this.Host` を使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって提供されるサービスと、読み込まれたパッケージまたは拡張機能にアクセスできます。  
  
 hostspecific\="true" を設定し、`this.Host` を <xref:System.IServiceProvider> にキャストします。  
  
 この例では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API である <xref:EnvDTE.DTE> をサービスとして取得します。  
  
```c#  
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
  
## テンプレートの継承があったホスト固有の使用  
 指定`hostspecific="trueFromBase"`もを使用する場合は、 `inherits`属性を指定のテンプレートから継承する場合は、 `hostspecific="true"`。  これは、コンパイラ警告が避けることができますは、プロパティ`Host` 2 回宣言されています。