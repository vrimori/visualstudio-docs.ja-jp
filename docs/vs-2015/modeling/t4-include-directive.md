---
title: T4 インクルード ディレクティブ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e8de721b7f26152cd4e7f5df1ee7eb4d04770511
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835944"
---
# <a name="t4-include-directive"></a>T4 インクルード ディレクティブ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] のテキスト テンプレートでは、`<#@include#>` ディレクティブを使用することによって、別のファイルのテキストをインクルードできます。 `include` ディレクティブは、テキスト テンプレートに含まれる最初のクラス機能ブロック (`<#+ ... #>`) の前の任意の場所に配置できます。 インクルード ファイルに、`include` ディレクティブや他のディレクティブを含めることもできます。 これにより、テンプレート間でテンプレート コードや定型句を共有できるようになります。  
  
## <a name="using-include-directives"></a>include ディレクティブの使用  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
- `filePath` には、絶対パスを指定することも、現在のテンプレート ファイルを基準とした相対パスを指定することもできます。  
  
   また、特定の [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 拡張機能で独自のディレクトリを指定して、インクルード ファイルを検索することもできます。 たとえば、Visualization and Modeling SDK (DSL) ツールをインストールしたら、次のフォルダーがインクルード一覧に追加されます:`Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`します。  
  
   追加されるこれらのインクルード フォルダーは、インクルード ファイルの拡張子によって異なります。 たとえば、DSL ツールのインクルード フォルダーは、インクルード ファイルの拡張子が `.tt` の場合にのみ追加されます。  
  
- `filePath` には、"%" で区切られた環境変数を含めることもできます。 例えば:  
  
  ```  
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
  ```  
  
- インクルード ファイルの名前に、拡張子 `".tt"` を使用する必要はありません。  
  
   必要に応じて、インクルード ファイルには、`".t4"` など別の拡張子を使用できます。 追加するため、これは、`.tt`ファイルをプロジェクト、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が自動的に設定その**カスタム ツール**プロパティを`TextTemplatingFileGenerator`。 通常、インクルード ファイルを個別に変換することは望ましくありません。  
  
   一方、ファイルの拡張子によって、インクルード ファイルの検索先となる追加フォルダーが決まる場合があることに注意してください。 これは、インクルード ファイルに他のファイルが含まれている場合に重要となります。  
  
- インクルードされたコンテンツは、インクルード先のテキスト テンプレートに元から含まれていた場合とほとんど同じように処理されます。 ただし、`<#+...#>` ディレクティブの後に通常のテキスト ブロックと標準コントロール ブロックが続く場合でも、クラス機能ブロック (`include`) を含むファイルをインクルードすることができます。  
  
- 他の複数のインクルード ファイルから起動された場合もテンプレートが 1 度だけインクルードされるようにするには、`once="true"` を使用します。  
  
   気にせずに含めることができる再利用可能な T4 スニペットのライブラリを構築することが容易には、この機能によりその他のいくつかのスニペットが既に含まれていること。  たとえば、テンプレート処理と c# 生成を処理する非常に詳細なスニペットのライブラリがあるとします。  さらに、これら複数のアプリケーション固有のすべてのテンプレートからを使用することができますし、例外を生成するなどのいくつかのタスク固有ではよりユーティリティによって使用されます。 依存関係グラフを描画すると、何回もインクルードされるスニペットがあることがわかります。 ただし、`once` パラメーターが指定されると、以降はインクルードが無効になります。  
  
  **MyTextTemplate.tt:**  
  
```  
<#@ output extension=".txt" #>  
Output message 1 (from top template).  
<#@ include file="TextFile1.t4"#>  
Output message 5 (from top template).  
<#  
   GenerateMessage(6); // defined in TextFile1.t4  
   AnotherGenerateMessage(7); // defined in TextFile2.t4  
#>  
  
```  
  
 **TextFile1.t4:**  
  
```  
   Output Message 2 (from included file).  
<#@include file="TextFile2.t4" #>  
   Output Message 4 (from included file).  
<#+ // Start of class feature control block.  
void GenerateMessage(int n)  
{  
#>  
   Output Message <#= n #> (from GenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **TextFile2.t4:**  
  
```  
        Output Message 3 (from included file 2).  
<#+ // Start of class feature control block.  
void AnotherGenerateMessage(int n)  
{  
#>  
       Output Message <#= n #> (from AnotherGenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **結果には、ファイル、MyTextTemplate.txt が生成されます。**  
  
```  
Output message 1 (from top template).  
   Output Message 2 (from included file).  
        Output Message 3 (from included file 2).  
  
   Output Message 4 (from included file).  
  
Output message 5 (from top template).  
   Output Message 6 (from GenerateMessage method).  
       Output Message 7 (from AnotherGenerateMessage method).  
  
```  
  
##  <a name="msbuild"></a> MSBuild および Visual Studio でプロジェクト プロパティの使用  
 include ディレクティブで $(SolutionDir) などの Visual Studio マクロを使用できますが、MSBuild では動作しません。 ビルド コンピューターでテンプレートを変換する場合、代わりにプロジェクトのプロパティを使用する必要があります。  
  
 .csproj ファイルまたは .vbproj ファイルを編集してプロジェクトのプロパティを定義します。 この例では、`myIncludeFolder` という名前のプロパティを定義します。  
  
```xml  
<!-- Define a project property, myIncludeFolder: -->  
<PropertyGroup>  
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myIncludeFolder">  
      <Value>$(myIncludeFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 これで、Visual Studio および MSBuild の両方で正しく変換できるテキスト テンプレートでプロジェクトのプロパティを使用できます。  
  
```  
<#@ include file="$(myIncludeFolder)\defs.tt" #>  
```



