---
title: "テキスト テンプレートから Visual Studio またはその他のホストにアクセスする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: "5"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 6b75a3b3e57ee72afc11013a1cf7a041b222b204
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>テキスト テンプレートから Visual Studio またはその他のホストへのアクセス
メソッドとように、テンプレートを実行するホストによって公開されるプロパティを使用する、テキスト テンプレートで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
 これは、通常のテキスト テンプレート、いない前処理されたテキスト テンプレートに適用されます。  
  
## <a name="obtaining-access-to-the-host"></a>ホストへのアクセスを取得します。  
 設定`hostspecific="true"`で、`template`ディレクティブです。 使用できます`this.Host`、型を持つ<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>します。 この型には、使用できる、たとえば、ファイル名を解決するのには、エラーをログにメンバーがあります。  
  
### <a name="resolving-file-names"></a>ファイル名を解決します。  
 テキスト テンプレートに関連するファイルの完全なパスを検索するには、これを使用します。Host.ResolvePath() です。  
  
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
  
### <a name="displaying-error-messages"></a>エラー メッセージを表示します。  
 この例は、テンプレートを変換するときにメッセージを記録します。 ホストがある場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、エラー ウィンドウに追加されます。  
  
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
  
## <a name="using-the-visual-studio-api"></a>Visual Studio API の使用  
 テキスト テンプレートを実行している場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、使用することができます`this.Host`によって提供されるサービスへのアクセス[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]とパッケージまたは読み込まれている拡張機能です。  
  
 設定 hostspecific ="true"とキャスト`this.Host`に<xref:System.IServiceProvider>です。  
  
 この例では取得、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API、 <xref:EnvDTE.DTE>、サービスとして。  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>テンプレートの継承で hostSpecific の使用  
 指定`hostspecific="trueFromBase"`使用する場合は、`inherits`属性を指定したテンプレートから継承する場合と`hostspecific="true"`です。 これは、影響を及ぼすコンパイラの警告を回避できますをプロパティ`Host`2 回宣言されています。