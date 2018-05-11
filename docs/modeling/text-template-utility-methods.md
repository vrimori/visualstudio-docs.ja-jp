---
title: テキスト テンプレートのユーティリティ メソッド
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9367c5c8e65c58a79b0d8e864c5a9a201fbe3954
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="text-template-utility-methods"></a>テキスト テンプレートのユーティリティ メソッド

Visual Studio テキスト テンプレートでコードを記述する場合は、常に使用できるいくつかの方法はあります。 これらのメソッドが定義されている<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>です。

> [!TIP]
> また、他のメソッドと正規 (いない前処理された) テキスト テンプレートでのホスト環境で提供されるサービスを使用することができます。 たとえば、ファイルのパスを解決するには、エラーをログに記録して Visual Studio やいずれかによって提供されるサービスを取得パッケージをロードします。 詳細については、次を参照してください。[テキスト テンプレートから Visual Studio のへのアクセス](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4)です。

## <a name="write-methods"></a>書き込みメソッド

使用することができます、`Write()`と`WriteLine()`式コード ブロックを使用する代わりに、標準のコード ブロック内のテキストを追加する方法です。 次の 2 つのコード ブロックは、機能的に等価です。

### <a name="code-block-with-an-expression-block"></a>式ブロックを含むコード ブロック

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>WriteLine() を使用してコード ブロック

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

入れ子になった制御構造を持つ長いコード ブロックの内部式ブロックの代わりにこれらのユーティリティ メソッドのいずれかを使用すると便利です。

`Write()`と`WriteLine()`メソッドが 2 つのオーバー ロードを持つ、複合書式指定文字列と、文字列に含めるオブジェクトの配列を受け取り、1 つの文字列パラメーターと 1 つを受け取るいずれか (のように、`Console.WriteLine()`メソッド)。 次の 2 つの使い方`WriteLine()`は機能的に同等です。

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>インデント メソッド

インデント メソッドを使用するには、テキスト テンプレートの出力を書式設定します。 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>クラスには、`CurrentIndent`テキスト テンプレートでの現在のインデントを示すプロパティを文字列と`indentLengths`フィールドが追加されているへこみの一覧です。 インデント設定を追加することができます、`PushIndent()`メソッドおよび減算で、インデント、`PopIndent()`メソッドです。 すべてのインデントを削除する場合を使用して、`ClearIndent()`メソッドです。 次のコード ブロックは、これらのメソッドの使用を示しています。

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

次のコード ブロックには、次の出力が生成されます。

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>エラーと警告メソッド

エラーと警告のユーティリティ メソッドを使用して、メッセージを Visual Studio のエラー一覧に追加することができます。 たとえば、次のコードは エラー一覧に、エラー メッセージを追加します。

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>ホストおよびサービス プロバイダーへのアクセス

プロパティ`this.Host`テンプレートを実行しているホストによって公開されるプロパティへのアクセスを提供できます。 使用する`this.Host`、設定する必要があります`hostspecific`属性、`<@template#>`ディレクティブ。

`<#@template ... hostspecific="true" #>`

型`this.Host`テンプレートを実行しているホストの種類によって異なります。 Visual Studio で実行されているテンプレートでキャストできます`this.Host`に`IServiceProvider`IDE などのサービスにアクセスするためにします。 例えば:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>別の一連のユーティリティ メソッドを使用します。

常に名前のクラスに変換された、テンプレート ファイル、テキストの生成処理の一環として、`GeneratedTextTransformation`から継承して<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>です。 別に使用するメソッドの代わりに、設定するは、独自のクラスを作成し、テンプレート ディレクティブに指定します。 クラスを継承する必要があります<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>です。

```
<#@ template inherits="MyUtilityClass" #>
```

使用して、`assembly`コンパイル済みのクラスが含まれるアセンブリを参照するディレクティブ。