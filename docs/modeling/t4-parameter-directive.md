---
title: "T4 パラメーター ディレクティブ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# T4 パラメーター ディレクティブ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のテキスト テンプレートでは、外部コンテキストから渡された値から初期化されるテンプレート コード内のプロパティを `parameter` ディレクティブで宣言します。  テキスト変換を呼び出すコードを作成する場合に、これらの値を設定できます。  
  
## parameter ディレクティブの使用  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 `parameter` ディレクティブでは、外部コンテキストから渡された値から初期化されるテンプレート コード内のプロパティを宣言します。  テキスト変換を呼び出すコードを作成する場合に、これらの値を設定できます。  値は、`Session` ディクショナリまたは <xref:System.Runtime.Remoting.Messaging.CallContext> に渡すことができます。  
  
 リモート処理可能な型のパラメーターを宣言できます。  つまり、<xref:System.SerializableAttribute> を使用して型を宣言するか、<xref:System.MarshalByRefObject> から型を派生する必要があります。  これにより、テンプレートを処理する AppDomain にパラメーター値を渡すことができるようになります。  
  
 たとえば、次の内容を含むテキスト テンプレートを作成できます。  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## テンプレートへのパラメーター値の引き渡し  
 メニュー コマンドやイベント ハンドラーなどの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 拡張機能を作成する場合は、テキスト テンプレート サービスを使用してテンプレートを処理できます。  
  
```c#  
// Get a service provider – how you do this depends on the context:  
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
  
## 呼び出しコンテキストへの値の引き渡し  
 値を論理データとして <xref:System.Runtime.Remoting.Messaging.CallContext> に渡すこともできます。  
  
 次の例では、両方の方法を使用して値を渡しています。  
  
```c#  
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
  
## 実行時 \(前処理された\) テキスト テンプレートへの値の引き渡し  
 通常、実行時 \(前処理された\) テキスト テンプレートで `<#@parameter#>` ディレクティブを使用する必要はありません。  代わりに、生成されたコードに対して追加のコンストラクターまたは設定可能なプロパティを定義し、これらを使用してパラメーター値を渡すことができます。  詳細については、「[T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)」を参照してください。  
  
 ただし、実行時テンプレートで `<#@parameter>` を使用する場合は、Session ディクショナリを使用してテンプレートに値を渡すことができます。  たとえば、`PreTextTemplate1` という前処理されたテンプレートとしてファイルを作成したとします。  この場合、次のコードを使用してプログラムでテンプレートを呼び出すことができます。  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## TextTemplate.exe からの引数の取得  
  
> [!IMPORTANT]
>  `parameter` ディレクティブでは、`TextTransform.exe` ユーティリティの `–a` パラメーターに設定された値は取得しません。  これらの値を取得するには、`template` ディレクティブで `hostSpecific="true"` を設定し、`this.Host.ResolveParameterValue("","","argName")` を使用します。