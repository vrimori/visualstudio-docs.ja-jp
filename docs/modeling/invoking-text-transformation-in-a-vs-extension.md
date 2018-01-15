---
title: "VS 拡張機能でテキスト変換の呼び出し |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 578c1aa9200640fc41392dc4046afe1793284f3c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>VS 拡張機能内でのテキスト変換の呼び出し
メニュー コマンドなどの Visual Studio 拡張機能を記述するかどうかまたは[ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)、テキスト テンプレートを変換するテキスト テンプレート サービスを使用することができます。 <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> サービスを取得し、<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating> にキャストします。  
  
## <a name="getting-the-text-templating-service"></a>テキスト テンプレート サービスの取得  
  
```csharp  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
  
// Process a text template:  
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));  
  
```  
  
## <a name="passing-parameters-to-the-template"></a>テンプレートへのパラメーターの引き渡し  
 パラメーターをテンプレートに渡すことができます。 テンプレート内で、`<#@parameter#>` ディレクティブを使用してパラメーター値を取得できます。  
  
 パラメーターの型については、シリアル化またはマーシャリング可能な型を使用する必要があります。 つまり、<xref:System.SerializableAttribute> を使用して型を宣言するか、<xref:System.MarshalByRefObject> から型を派生する必要があります。 この制限が必要なのは、テキスト テンプレートは別の AppDomain で実行されるためです。 などのすべての組み込み型**System.String**と**System.Int32**はシリアル化します。  
  
 パラメーター値を渡すために、呼び出し元のコードでは `Session` ディクショナリまたは <xref:System.Runtime.Remoting.Messaging.CallContext> に値を配置できます。  
  
 次の例では、両方の方法を使用して短いテスト テンプレートを変換しています。  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = dte;   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;  
  
// Create a Session in which to pass parameters:  
sessionHost.Session = sessionHost.CreateSession();  
sessionHost.Session["parameter1"] = "Hello";  
sessionHost.Session["parameter2"] = DateTime.Now;  
  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);  
  
// Process a text template:  
string result = t4.ProcessTemplate("",  
   // This is the test template:  
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"  
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"  
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"  
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");  
  
// This test code yields a result similar to the following line:  
//     Test: Hello    07/06/2010 12:37:45    42  
  
```  
  
## <a name="error-reporting-and-the-output-directive"></a>エラー報告と出力ディレクティブ  
 処理中にエラーが発生すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のエラー ウィンドウに表示されます。 また、<xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback> を実装したコールバックを指定することにより、エラーの通知を受けることもできます。  
  
 結果の文字列をファイルに書き込む場合は、テンプレートの `<#@output#>` ディレクティブで指定されているファイル拡張子とエンコードを確認できます。 この情報は、コールバックにも渡されます。 詳細については、次を参照してください。 [T4 出力ディレクティブ](../modeling/t4-output-directive.md)です。  
  
```csharp  
void ProcessMyTemplate(string MyTemplateFile)  
{  
  string templateContent = File.ReadAllText(MyTemplateFile);  
  T4Callback cb = new T4Callback();  
  // Process a text template:  
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);  
  // If there was an output directive in the MyTemplateFile,  
  // then cb.SetFileExtension() will have been called.  
  // Determine the output file name:  
  string resultFileName =   
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),   
        Path.GetFileNameWithoutExtension(MyTemplateFile))   
      + cb.fileExtension;  
  // Write the processed output to file:  
  File.WriteAllText(resultFileName, result, cb.outputEncoding);  
  // Append any error messages:  
  if (cb.errorMessages.Count > 0)  
  {  
    File.AppendAllLines(resultFileName, cb.errorMessages);  
  }  
}  
  
class T4Callback : ITextTemplatingCallback  
{  
  public List<string> errorMessages = new List<string>();  
  public string fileExtension = ".txt";  
  public Encoding outputEncoding = Encoding.UTF8;  
  
  public void ErrorCallback(bool warning, string message, int line, int column)  
  { errorMessages.Add(message); }  
  
  public void SetFileExtension(string extension)  
  { fileExtension = extension; }  
  
  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)  
  { outputEncoding = encoding; }  
}  
  
```  
  
 次のようなテンプレート ファイルを使用してコードをテストできます。  
  
```  
<#@output extension=".htm" encoding="ASCII"#>  
<# int unused;  // Compiler warning "unused variable"  
#>  
Sample text.  
```  
  
 コンパイラの警告は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のエラー ウィンドウに表示されます。また、コンパイラの警告によって、`ErrorCallback` の呼び出しも生成されます。  
  
## <a name="reference-parameters"></a>参照パラメーター  
 <xref:System.MarshalByRefObject> から派生したパラメーター クラスを使用して、テキスト テンプレートの外部に値を渡すことができます。  
  
## <a name="related-topics"></a>関連トピック  
 前処理されたテキスト テンプレートからテキストを生成するには  
 生成されたクラスの `TransformText()` メソッドを呼び出します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)です。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 拡張機能の範囲外でテキストを生成するには  
 カスタム ホストを定義します。 詳細については、次を参照してください。[カスタム ホストを使用してテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)です。  
  
 後でコンパイルして実行できるソース コードを生成するには  
 `t4.PreprocessTemplate()` の <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating> メソッドを呼び出します。
