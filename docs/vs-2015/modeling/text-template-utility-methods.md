---
title: テキスト テンプレートのユーティリティ メソッド |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 98506212abe977b16a2c580ae16075b557eb3c2a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544847"
---
# <a name="text-template-utility-methods"></a>テキスト テンプレートのユーティリティ メソッド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[テキスト テンプレートのユーティリティ メソッド](https://docs.microsoft.com/visualstudio/modeling/text-template-utility-methods)します。  
  
コードを記述するときに使用可能な常にいくつかのメソッドがある、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]テキスト テンプレート。 これらのメソッドが定義されている<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>します。  
  
> [!TIP]
>  他のメソッドと正規表現 (いない前処理された) テキスト テンプレートでのホスト環境によって提供されるサービスを使用することもできます。 たとえば、ファイル パスを解決、エラーをログに記録してによって提供されるサービスを取得[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]といずれかのパッケージが読み込まれます。  詳細については、次を参照してください。[テキスト テンプレートから Visual Studio のへのアクセス](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4)します。  
  
## <a name="write-methods"></a>メソッドを記述します。  
 使用することができます、`Write()`と`WriteLine()`式のコード ブロックを使用する代わりに、標準のコード ブロック内でテキストを追加する方法。 次の 2 つのコード ブロックは、機能的に同等です。  
  
##### <a name="code-block-with-an-expression-block"></a>式ブロックのコード ブロック  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>WriteLine() を使用してコード ブロック  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 入れ子になった制御構造を持つ長いコード ブロック内で式ブロックの代わりにこれらのユーティリティ メソッドのいずれかを使用すると便利です。  
  
 `Write()`と`WriteLine()`メソッドは、2 つのオーバー ロードが場合、複合書式指定文字列と、文字列に含めるオブジェクトの配列を受け取り、1 つの文字列パラメーターと 1 つを受け取るいずれか (など、`Console.WriteLine()`メソッド)。 次の 2 つの用途の`WriteLine()`は機能的に同等です。  
  
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
 インデント メソッドを使用するには、テキスト テンプレートの出力を書式設定します。 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>クラスには、`CurrentIndent`文字列テキスト テンプレートでの現在のインデントの位置を示すプロパティと`indentLengths`フィールドに追加されているインデントの一覧。 インデントを追加することができます、`PushIndent()`メソッドおよび減算で、インデント、`PopIndent()`メソッド。 すべてのインデントを削除する場合を使用して、`ClearIndent()`メソッド。 次のコード ブロックは、これらのメソッドの使用を示しています。  
  
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
  
 このコード ブロックには、次の出力が生成されます。  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>エラーと警告メソッド  
 エラーおよび警告のユーティリティ メソッドを使用してへのメッセージを追加することができます、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]エラー一覧。 たとえば、次のコードは エラー一覧に、エラー メッセージを追加します。  
  
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
  
## <a name="access-to-host-and-service-provider"></a>ホストとサービス プロバイダーへのアクセス  
 プロパティ`this.Host`テンプレートを実行しているホストによって公開されるプロパティにアクセスできるようにします。 使用する`this.Host`を設定する必要があります`hostspecific`属性、`<@template#>`ディレクティブ。  
  
 `<#@template ... hostspecific="true" #>`  
  
 型`this.Host`テンプレートを実行しているホストの種類によって異なります。 実行されているテンプレートで[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、キャストできます`this.Host`に`IServiceProvider`IDE などのサービスにアクセスします。 例えば:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>さまざまなユーティリティ メソッドを使用します。  
 名前は常に、クラスに、テンプレート ファイルを変換、テキスト生成処理の一環として、`GeneratedTextTransformation`から継承して<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>します。 別に使用するメソッドの代わりに、設定するは、独自のクラスを記述し、template ディレクティブで指定します。 クラスを継承する必要があります<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>します。  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 使用して、`assembly`コンパイル済みのクラスがあるアセンブリを参照するディレクティブ。



