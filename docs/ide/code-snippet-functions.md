---
title: "コード スニペットの関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード スニペット [Visual Studio], 関数"
  - "IntelliSense コード スニペット, 関数"
  - "スニペット [Visual Studio], 関数"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# コード スニペットの関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] コード スニペットで使用できる関数は 3 つあります。  関数は、コード スニペットの[Function](http://msdn.microsoft.com/ja-jp/572c5549-5821-4e15-8ecd-0fa86c1c65df)で指定されています。  コード スニペットの作成については、「[コード スニペット](../ide/code-snippets.md)」を参照してください。  
  
## 関数  
 次の表は、コード スニペットの `Function` 要素で使用できる関数を示します。  
  
|Function|Description|言語|  
|--------------|-----------------|--------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|`EnumerationLiteral` パラメーターで指定された列挙体のメンバー用に、switch ステートメントおよび一連の case ステートメントを生成します。  `EnumerationLiteral` パラメーターは、列挙体リテラルまたは列挙型のどちらかへの参照にする必要があります。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|挿入されたスニペットが格納されているクラスの名前を返します。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|*TypeName* パラメーターを、スニペットが呼び出されたコンテキストで最も単純な形式に縮小します。|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## 使用例  
 `GenerateSwitchCases` 関数を使用する方法を次の例に示します。  このスニペットが挿入され、列挙体が `$switch_on$` リテラルに入力されると、`$cases$` リテラルによって列挙体の値ごとに `case` ステートメントが生成されます。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 使用例  
 `ClassName` 関数を使用する方法を次の例に示します。  このスニペットが挿入されると、`$classname$` リテラルは、コード ファイルでその位置にある外側のクラスの名前で置換されます。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 使用例  
 `SimpleTypeName` 関数を使用する方法の例を次に示します。  このスニペットがコード ファイルに挿入されると、`$SystemConsole$` リテラルは、このスニペットが呼び出されたコンテキストで最も単純な形式の <xref:System.Console> 型で置換されます。  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## 参照  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/ja-jp/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)