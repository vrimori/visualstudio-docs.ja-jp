---
title: "ProjectItem 要素 (Visual Studio プロジェクト テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> 要素 [Visual Studio プロジェクト テンプレート]"
  - "ProjectItem 要素 [Visual Studio プロジェクト テンプレート]"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# ProjectItem 要素 (Visual Studio プロジェクト テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロジェクト テンプレートに含まれているファイルを指定します。  
  
> [!NOTE]
>  `ProjectItem` 要素は、テンプレートがプロジェクト用かアイテム用かによって受け入れる属性が異なります。  ここでは、プロジェクト テンプレートの `ProjectItem` 要素について説明します。  項目テンプレートの `ProjectItem` 要素については、「[ProjectItem 要素 \(Visual Studio 項目テンプレート\)](../extensibility/projectitem-element-visual-studio-item-templates.md)」を参照してください。  
  
## 構文  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`TargetFileName`|省略可能な属性です。<br /><br /> テンプレートからプロジェクトを作成するときのプロジェクト アイテムの名前とパスを指定します。  この属性は、テンプレート .zip ファイルと異なるディレクトリ構造を作成する場合、またはアイテム名作成のためにパラメーター置換をする場合に便利です。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> ブール値を使用します。これは、プロジェクトがテンプレートから作成されるときに、置換する必要のあるパラメーター値がアイテムに存在するかどうかを指定します。  既定値は `false`です。|  
|`OpenInEditor`|省略可能な属性です。<br /><br /> ブール値を使用します。これは、プロジェクトがテンプレートから作成されるときに、アイテムを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内のアイテムに適切なエディターで開くかどうかを指定します。<br /><br /> `OpenInEditor` が `true` のアイテムでは、`OpenInWebBrowser` 属性および `OpenInHelpBrowser` 属性は無視されます。<br /><br /> 既定値 `false` です。|  
|`OpenInWebBrowser`|省略可能な属性です。<br /><br /> ブール値を使用します。これは、プロジェクトがテンプレートから作成されるときに、アイテムを Web ブラウザーで開くかどうかを指定します。<br /><br /> Web ブラウザーで開けるファイルは、プロジェクトにローカルの HTML ファイルとテキスト ファイルだけです。  外部 URL は、この属性では開くことができません。<br /><br /> 既定値 `false` です。|  
|`OpenInHelpBrowser`|省略可能な属性です。<br /><br /> ブール値を使用します。これは、プロジェクトがテンプレートから作成されるときに、アイテムをヘルプ ビューアーで開くかどうかを指定します。<br /><br /> ヘルプ ブラウザーで開けるファイルは、プロジェクトにローカルの HTML ファイルとテキスト ファイルだけです。  外部 URL は、この属性では開くことができません。<br /><br /> 既定値 `false` です。|  
|`OpenOrder`|省略可能な属性です。<br /><br /> エディターに開くアイテムの順番を示した数値を指定します。  すべての値は、10 の倍数である必要があります。  `OpenOrder` の高い値の項目は先に開きます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|プロジェクトに追加するファイルやディレクトリを指定します。|  
  
## テキスト値  
 テキスト値が必要です。  
  
 `string` は、テンプレート .zip ファイルにあるファイルの名前またはパスを示します。  
  
## 解説  
 `ProjectItem` は `Project` の省略可能な子要素です。  
  
 `TargetFileName` 属性は、テンプレート .zip ファイルと異なるディレクトリ構造を作成する場合に使用します。  たとえば、`MyFile.vb` というファイルがテンプレート .zip ファイルのルートにあるとします。このファイルを、テンプレートから作成したすべてのプロジェクトで `CustomFiles` というディレクトリに置くには、次の XML を使用します。  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 また、`TargetFileName` 属性を使用すると、ファイル名に各種言語の文字を含むファイルの名前を変更できます。  たとえば、テンプレート .zip ファイルには Unicode 文字を使用した名前を付けることができないため、ファイルを .zip ファイルに圧縮する前に名前を変更する必要があります。  `TargetFileName` 属性を使用すると、ファイル名を元の Unicode 文字を使用したファイル名に戻すことができます。  
  
 `TargetFileName` 属性は、パラメーターでファイルの名前を変更する場合にも使用できます。  次の手順は、テンプレート .zip ファイルのルート ディレクトリにある `MyFile.vb` ファイルの名前を、プロジェクト名に基づいたファイル名に変更する方法を説明しています。  
  
### パラメーターでファイルの名前を変更するには  
  
1.  .vstemplate ファイルで次の XML を使用します。  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  テキスト エディターまたは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクト ファイル \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロジェクトの場合は .vbproj\) を開きます。  
  
3.  プロジェクト ファイルで、次の XML のような行を探します。  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  このコード行を次の XML に置き換えます。  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     このテンプレートからプロジェクトを作成すると、プロジェクトには、**\[新しいプロジェクト\]** ダイアログ ボックスで入力した名前に基づいたファイル名が付きます。この際、ファイル名として使用できない文字やスペースはすべてファイル名から省かれます。  詳細については、「[テンプレート名](../ide/template-parameters.md)」を参照してください。  
  
## 使用例  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [テンプレート名](../ide/template-parameters.md)   
 [ProjectItem 要素 \(Visual Studio 項目テンプレート\)](../extensibility/projectitem-element-visual-studio-item-templates.md)