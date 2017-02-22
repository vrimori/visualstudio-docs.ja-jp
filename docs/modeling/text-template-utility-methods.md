---
title: "テキスト テンプレートのユーティリティ メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, ユーティリティ メソッド"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
caps.handback.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# テキスト テンプレートのユーティリティ メソッド
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] テキスト テンプレートにコードを記述するときにいつでも使用できるメソッドがいくつかあります。  これらのメソッドは、<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> で定義されます。  
  
> [!TIP]
>  標準の \(前処理されていない\) テキスト テンプレートでは、ホスト環境で提供される他のメソッドやサービスを使用することもできます。  たとえば、ファイル パスの解決、エラー ログの記録、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] や読み込まれた任意のパッケージで提供されるサービスの取得などを行うことができます。  詳細については、「[Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/ja-jp/0556f20c-fef4-41a9-9597-53afab4ab9e4)」を参照してください。  
  
## Write メソッド  
 `Write()` メソッドおよび `WriteLine()` メソッドを使用すると、式コード ブロックを使用する代わりに、標準コード ブロック内にテキストを追加できます。  次の 2 つのコード ブロックは、機能的には同じです。  
  
##### 式ブロックを含むコード ブロック  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### WriteLine\(\) を使用するコード ブロック  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 制御構造が入れ子になった長いコード ブロック内では、式ブロックの代わりにこれらのユーティリティ メソッドのいずれかを使用すると役に立つことがあります。  
  
 `Write()` メソッドと `WriteLine()` メソッドには 2 つのオーバーロードがあり、1 つは単一の文字列パラメーターを受け取り、もう 1 つは、\(`Console.WriteLine()` メソッドのように\) 複合書式指定文字列と、文字列に含めるオブジェクトの配列を受け取ります。  次の例では `WriteLine()` が 2 回使用されていますが、どちらも機能は同じです。  
  
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
  
## インデント メソッド  
 インデント メソッドを使用すると、テキスト テンプレートの出力を書式設定できます。  <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> クラスには、テキスト テンプレートでの現在のインデントを示す `CurrentIndent` 文字列プロパティと、追加されたインデントのリストである `indentLengths` フィールドがあります。  インデントの追加には `PushIndent()`  メソッドを使用し、インデントの削除には `PopIndent()` メソッドを使用します。  すべてのインデントを削除する場合は、`ClearIndent()` メソッドを使用します。  次のコード ブロックに、これらのメソッドの使用方法を示します。  
  
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
  
 このコード ブロックによって、次の出力が生成されます。  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## エラー メソッドと警告メソッド  
 エラーと警告のユーティリティ メソッドを使用すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の \[エラー一覧\] にメッセージを追加できます。  たとえば、次のコードは、\[エラー一覧\] にエラー メッセージを追加します。  
  
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
  
## ホストおよびサービス プロバイダーへのアクセス  
 `this.Host` プロパティでは、テンプレートを実行しているホストによって公開されるプロパティへのアクセスを提供できます。  `this.Host` を使用するには、`<@template#>` ディレクティブで `hostspecific` 属性を設定する必要があります。  
  
 `<#@template ...  hostspecific="true" #>`  
  
 `this.Host` の型は、テンプレートが実行されているホストの種類によって決まります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で実行されているテンプレートでは、`this.Host` を `IServiceProvider` にキャストすることにより、IDE などのサービスへのアクセスを取得できます。  次に例を示します。  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## 別のユーティリティ メソッド セットの使用  
 テキストの生成プロセスの一部として、テンプレート ファイルはクラスに変換されます。このクラスは常に `GeneratedTextTransformation` という名前になり、<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> から継承されます。  別のメソッドのセットを使用する場合は、独自のクラスを記述し、それをテンプレート ディレクティブで指定します。  このクラスは、<xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> を継承している必要があります。  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 コンパイル済みのクラスが含まれるアセンブリを参照するには、`assembly` ディレクティブを使用します。