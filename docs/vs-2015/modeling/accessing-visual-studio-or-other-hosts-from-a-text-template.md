---
title: テキスト テンプレートから Visual Studio または他のホストへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5bcd1811db000b39f7c9897f1329434af9fe5258
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538682"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>テキスト テンプレートから Visual Studio またはその他のホストへのアクセス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[にアクセスする Visual Studio または他のテキスト テンプレート ホスト](https://docs.microsoft.com/visualstudio/modeling/accessing-visual-studio-or-other-hosts-from-a-text-template)します。  
  
メソッドとなど、テンプレートを実行するホストによって公開されるプロパティを使用する、テキスト テンプレートで[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
 これは、通常のテキスト テンプレート、いない前処理されたテキスト テンプレートに適用されます。  
  
## <a name="obtaining-access-to-the-host"></a>ホストへのアクセスを取得します。  
 設定`hostspecific="true"`で、`template`ディレクティブ。 使用できる`this.Host`、型を持つ<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>します。 この型は、使用できる、たとえば、ファイル名を解決するのには、エラーをログにメンバーがあります。  
  
### <a name="resolving-file-names"></a>ファイル名を解決します。  
 テキスト テンプレートに関連するファイルの完全なパスを検索するには、これを使用します。Host.ResolvePath() します。  
  
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
 この例は、テンプレートを変換するときにメッセージを記録します。 ホストが場合[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、エラー ウィンドウに追加されます。  
  
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
  
## <a name="using-the-visual-studio-api"></a>Visual Studio API を使用  
 テキスト テンプレートを実行している場合[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、使用することができます`this.Host`によって提供されるサービスへのアクセス[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]とパッケージまたは読み込まれている拡張機能。  
  
 設定 hostspecific ="true"とキャスト`this.Host`に<xref:System.IServiceProvider>します。  
  
 この例の取得、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API、 <xref:EnvDTE.DTE>、サービスとして。  
  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>テンプレートの継承を持つ hostSpecific を使用します。  
 指定`hostspecific="trueFromBase"`も使用する場合、`inherits`属性を指定するテンプレートから継承する場合と`hostspecific="true"`します。 効果にコンパイラの警告を回避できるプロパティ`Host`は 2 回宣言されています。



