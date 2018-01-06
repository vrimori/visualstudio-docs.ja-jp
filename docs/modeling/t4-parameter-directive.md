---
title: "T4 パラメーター ディレクティブ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 434adf94f813c28f696a3218500428d659d68ddf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="t4-parameter-directive"></a>T4 パラメーター ディレクティブ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレート、`parameter`ディレクティブがテンプレート コードの外部のコンテキストから渡された値から初期化されるプロパティを宣言します。 テキスト変換を呼び出すコードを記述する場合、これらの値を設定することができます。  
  
## <a name="using-the-parameter-directive"></a>パラメーター ディレクティブの使用  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 `parameter`ディレクティブがテンプレート コードの外部のコンテキストから渡された値から初期化されるプロパティを宣言します。 テキスト変換を呼び出すコードを記述する場合、これらの値を設定することができます。 いずれかの値を渡すことができます、`Session`のディクショナリまたは<xref:System.Runtime.Remoting.Messaging.CallContext>です。  
  
 任意のリモート処理可能な型のパラメーターを宣言することができます。 型を宣言する必要があります<xref:System.SerializableAttribute>、またはそれから派生する必要があります、<xref:System.MarshalByRefObject>です。 これにより、テンプレートを処理する AppDomain に渡されるパラメーターの値です。  
  
 たとえば、次の内容のテキスト テンプレートを作成します。  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>テンプレートにパラメーター値を渡す  
 作成している場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]メニュー コマンドやイベント ハンドラーなどの拡張機能は、テキスト テンプレート サービスを使用してテンプレートを処理することができます。  
  
```csharp  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## <a name="passing-values-in-the-call-context"></a>呼び出すコンテキストに値を渡す  
 代わりに値を渡すことで、論理データ<xref:System.Runtime.Remoting.Messaging.CallContext>です。  
  
 次の例では、両方のメソッドを使用して値を渡します。  
  
```csharp  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>実行時 (前処理済み) テキスト テンプレートに値を渡す  
 通常、使用する必要はありません、`<#@parameter#>`実行時 (前処理された) テキスト テンプレートのディレクティブ。 代わりに、追加のコンス トラクターまたはパラメーターの値を通過する、生成されたコードの設定可能なプロパティを定義できます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)です。  
  
 ただし、使用する場合`<#@parameter>`実行時テンプレートにするに渡すこと値セッション ディクショナリを使用しています。 例として、たとえば、ファイルと呼ばれるプリプロセス済みのテンプレートとして作成した`PreTextTemplate1`です。 次のコードを使用して、プログラムでは、テンプレートを呼び出すことができます。  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>TextTemplate.exe から引数を取得します。  
  
> [!IMPORTANT]
>  `parameter`ディレクティブで設定された値を取得しません、`-a`のパラメーター、`TextTransform.exe`ユーティリティです。 これらの値を取得するには、次のように設定します。`hostSpecific="true"`で、`template`ディレクティブ、および使用`this.Host.ResolveParameterValue("","","argName")`です。