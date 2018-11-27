---
title: T4 パラメーター ディレクティブ
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2db812268b991d6160e515da5a3922ef47bb7a13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886527"
---
# <a name="t4-parameter-directive"></a>T4 パラメーター ディレクティブ

Visual Studio テキスト テンプレートで、`parameter`ディレクティブは、外部のコンテキストから渡された値で初期化される テンプレート コードのプロパティを宣言します。 テキスト変換を呼び出すコードを記述する場合は、これらの値を設定できます。

## <a name="using-the-parameter-directive"></a>パラメーター ディレクティブの使用

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter`ディレクティブは、テンプレート コードの外部のコンテキストから渡された値により初期化されるプロパティを宣言します。 テキスト変換を呼び出すコードを記述する場合は、これらの値を設定できます。 値としては`Session`ディクショナリ、または <xref:System.Runtime.Remoting.Messaging.CallContext> のいずれかを渡すことができます。

 任意のリモート処理可能な型のパラメーターを宣言することができます。 すなわち、型は <xref:System.SerializableAttribute> をもって宣言されるか、<xref:System.MarshalByRefObject> から派生する必要があります。 これにより、テンプレートを処理する AppDomain にパラメーターの値を渡すことが許されます。

 たとえば、次の内容のテキスト テンプレートを記述できます。

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>テンプレートにパラメーター値を渡す
 メニュー コマンドやイベント ハンドラーなどの Visual Studio 拡張機能を作成する場合は、テキスト テンプレート サービスを使用してテンプレートを処理できます。

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

## <a name="passing-values-in-the-call-context"></a>呼び出しコンテキストで値を渡す
 <xref:System.Runtime.Remoting.Messaging.CallContext> 中で論理データとして値を渡すこともできます。

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>ランタイム (前処理された) テキスト テンプレートに値を渡す
 通常、ランタイム (前処理された) テキスト テンプレートで `<#@parameter#>`ディレクティブを使用する必要はありません。 代わりに、生成されたコードに対して追加のコンストラクターや設定可能なプロパティを定義し、パラメーターの値を渡すことができます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)

 ただし、ランタイムテンプレートで `<#@parameter>` を使用する場合、`Session`ディクショナリを使用して渡すこともできます。 例として、 `PreTextTemplate1` という名前の前処理済みテンプレートとしてファイルを作成したとします。 テンプレートは、次のコードを使用して、プログラムで呼び出すことができます。

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
>  `parameter`ディレクティブは、`TextTransform.exe`ユーティリティの`-a`のパラメーターで設定された値を取得できません。 これらの値を取得するには、`template`ディレクティブで、`hostSpecific="true"` を設定し、`this.Host.ResolveParameterValue("","","argName")` を使用します。
