---
title: "テキスト テンプレートのユーティリティ メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: "50"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: cff244ea8b3ba8e6dd25af06d51bf5b80b51aa06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="text-template-utility-methods"></a>テキスト テンプレートのユーティリティ メソッド
コードを記述する場合は、常に使用できるいくつかの方法がある、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキスト テンプレートです。 これらのメソッドが定義されている<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>です。  
  
> [!TIP]
>  また、他のメソッドと正規 (いない前処理された) テキスト テンプレートでのホスト環境で提供されるサービスを使用することができます。 たとえば、ファイルのパスを解決するには、エラーをログに記録してによって提供されるサービスを取得[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パッケージを読み込むとします。  詳細については、次を参照してください。[テキスト テンプレートから Visual Studio のへのアクセス](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4)です。  
  
## <a name="write-methods"></a>書き込みメソッド  
 使用することができます、`Write()`と`WriteLine()`式コード ブロックを使用する代わりに、標準のコード ブロック内のテキストを追加する方法です。 次の 2 つのコード ブロックは、機能的に等価です。  
  
##### <a name="code-block-with-an-expression-block"></a>式ブロックを含むコード ブロック  
  
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
 エラーおよび警告のユーティリティ メソッドを使用してメッセージを追加することができます、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エラー ボックスの一覧です。 たとえば、次のコードは エラー一覧に、エラー メッセージを追加します。  
  
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
  
 型`this.Host`テンプレートを実行しているホストの種類によって異なります。 実行されているテンプレートで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、キャストできます`this.Host`に`IServiceProvider`IDE などのサービスにアクセスするためにします。 例:  
  
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