---
title: T4 アセンブリ ディレクティブ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2d0588688a6545471cfaa480d0efac868fe708de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="t4-assembly-directive"></a>T4 アセンブリ ディレクティブ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデザイン時テキスト テンプレートでは、テンプレート コードでアセンブリの型を使用できるように、`assembly` ディレクティブによってアセンブリが読み込まれます。 結果は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトでアセンブリ参照を追加した場合と同様です。  
  
 テキスト テンプレートの記述の一般的な概要については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)です。  
  
> [!NOTE]
>  実行時 (前処理された) テキスト テンプレートでは、`assembly` ディレクティブは不要です。 代わりに必要なアセンブリを追加、**参照**の[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。  
  
## <a name="using-the-assembly-directive"></a>assembly ディレクティブの使用  
 ディレクティブの構文は次のとおりです。  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 アセンブリ名は、次のいずれかであることが必要です。  
  
-   GAC のアセンブリの厳密な名前 (`System.Xml.dll` など)。 `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"` のような長い形式を使用することもできます。 詳細については、「<xref:System.Reflection.AssemblyName>」を参照してください。  
  
-   アセンブリの絶対パス。  
  
 `$(variableName)` 構文を使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の変数 (`$(SolutionDir)` など) を参照し、`%VariableName%` を使用して環境変数を参照できます。 例えば:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 assembly ディレクティブは、前処理されたテキスト テンプレートでは無効です。 代わりに、必要な参照が含まれて、**参照**のセクションで、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)です。  
  
## <a name="standard-assemblies"></a>標準アセンブリ  
 次のアセンブリは自動的に読み込まれるので、これらのアセンブリのアセンブリ ディレクティブを記述する必要はありません。  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 カスタム ディレクティブを使用する場合は、ディレクティブ プロセッサによって追加のアセンブリが読み込まれます。 たとえば、ドメイン固有言語 (DSL) のテンプレートを作成した場合、次のアセンブリのアセンブリ ディレクティブを記述する必要はありません。  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   DSL を含むアセンブリ  
  
##  <a name="msbuild"></a> MSBuild および Visual Studio の両方でのプロジェクト プロパティの使用  
 Visual Studio のマクロ $ (solutiondir) などは、MSBuild で動作しません。 ビルド コンピューターでテンプレートを変換する場合、代わりにプロジェクトのプロパティを使用する必要があります。  
  
 .csproj ファイルまたは .vbproj ファイルを編集してプロジェクトのプロパティを定義します。 この例では、`myLibFolder` という名前のプロパティを定義します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [T4 インクルード ディレクティブ](../modeling/t4-include-directive.md)