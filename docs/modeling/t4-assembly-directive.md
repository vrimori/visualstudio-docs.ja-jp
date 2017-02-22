---
title: "T4 アセンブリ ディレクティブ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 4
caps.handback.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 アセンブリ ディレクティブ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデザイン時テキスト テンプレートでは、テンプレート コードでアセンブリの型を使用できるように、`assembly` ディレクティブによってアセンブリが読み込まれます。  結果は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトでアセンブリ参照を追加した場合と同様です。  
  
 テキスト テンプレートの作成方法の概要については、「[T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)」を参照してください。  
  
> [!NOTE]
>  実行時 \(前処理された\) テキスト テンプレートでは、`assembly` ディレクティブは不要です。  代わりに、必要なアセンブリを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトの **\[参照\]** に追加します。  
  
## assembly ディレクティブの使用  
 ディレクティブの構文は次のとおりです。  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 アセンブリ名は、次のいずれかであることが必要です。  
  
-   GAC のアセンブリの厳密な名前 \(`System.Xml.dll` など\)。  `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"` のような長い形式を使用することもできます。  詳細については、「<xref:System.Reflection.AssemblyName>」を参照してください。  
  
-   アセンブリの絶対パス。  
  
 `$(variableName)` 構文を使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の変数 \(`$(SolutionDir)` など\) を参照し、`%VariableName%` を使用して環境変数を参照できます。  次に例を示します。  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 assembly ディレクティブは、前処理されたテキスト テンプレートでは無効です。  必要な参照は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトの **\[参照\]** セクションで追加してください。  詳細については、「[T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)」を参照してください。  
  
## 標準アセンブリ  
 次のアセンブリは自動的に読み込まれるので、これらのアセンブリのアセンブリ ディレクティブを記述する必要はありません。  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 カスタム ディレクティブを使用する場合は、ディレクティブ プロセッサによって追加のアセンブリが読み込まれます。  たとえば、ドメイン固有言語 \(DSL\) のテンプレートを作成した場合、次のアセンブリのアセンブリ ディレクティブを記述する必要はありません。  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   DSL を含むアセンブリ  
  
##  <a name="msbuild"></a> MSBuild および Visual Studio の両方でのプロジェクト プロパティの使用  
 $\(SolutionDir\) などの Visual Studio のマクロは、MSBuild では動作しません。  ビルド コンピューターでテンプレートを変換する場合、代わりにプロジェクトのプロパティを使用する必要があります。  
  
 .csproj ファイルまたは .vbproj ファイルを編集してプロジェクトのプロパティを定義します。  この例では、`myLibFolder` という名前のプロパティを定義します。  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 これで、Visual Studio および MSBuild の両方で正しく変換できるテキスト テンプレートでプロジェクトのプロパティを使用できます。  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## 参照  
 [T4 インクルード ディレクティブ](../modeling/t4-include-directive.md)