---
title: "ProjectItem 要素 (Visual Studio プロジェクト テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ca5143a3e5eaff488fee89b643a40adb60473bd8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 要素 (Visual Studio プロジェクト テンプレート)
プロジェクト テンプレートに含まれているファイルを指定します。  
  
> [!NOTE]
>  `ProjectItem`要素は、テンプレートが、プロジェクトまたは項目があるかによって異なる属性を受け入れます。 このトピックの内容について説明します、`ProjectItem`プロジェクト テンプレートの要素。 詳細について、`ProjectItem`項目テンプレートの要素を参照してください[ProjectItem 要素 (Visual Studio 項目テンプレート)](../extensibility/projectitem-element-visual-studio-item-templates.md)です。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<ProjectItem >  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`TargetFileName`|省略可能な属性です。<br /><br /> テンプレートからプロジェクトの作成時に、プロジェクト項目のパスと名前を指定します。 この属性は、テンプレート .zip ファイルのディレクトリ構造からさまざまなディレクトリ構造を作成するため、またはパラメーター置換を使用して、アイテムの名前を作成するのに便利です。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> アイテムが、テンプレートからプロジェクトの作成時に置き換える必要があるパラメーターの値があるかどうかを指定するブール値。 既定値は `false`にする必要があります。|  
|`OpenInEditor`|省略可能な属性です。<br /><br /> 項目をそれぞれのエディターで開く必要があるかどうかを指定するブール値[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テンプレートからプロジェクトを作成するときにします。<br /><br /> `OpenInWebBrowser`と`OpenInHelpBrowser`を持つ項目の属性は無視されます、`OpenInEditor`値`true`です。<br /><br /> 既定値は `false` です。|  
|`OpenInWebBrowser`|省略可能な属性です。<br /><br /> かどうか、項目開かなければなりません Web ブラウザー、テンプレートからプロジェクトの作成時に指定するブール値。<br /><br /> Web ブラウザーでは、HTML ファイルおよびプロジェクトに対してローカルなテキスト ファイルだけを開くことができます。 この属性では、外部 Url を開くことができません。<br /><br /> 既定値は `false` です。|  
|`OpenInHelpBrowser`|省略可能な属性です。<br /><br /> テンプレートからプロジェクトの作成時に、アイテムをヘルプ ビューアーで開く必要があるかどうかを指定するブール値。<br /><br /> HTML ファイルおよびプロジェクトに対してローカルなテキスト ファイルだけは、ヘルプ ブラウザーで開くことができます。 この属性では、外部 Url を開くことができません。<br /><br /> 既定値は `false` です。|  
|`OpenOrder`|省略可能な属性です。<br /><br /> 項目はエディターに表示する順序を表す数値を指定します。 すべての値は 10 の倍数である必要があります。 以降の項目`OpenOrder`値が最初に開きます。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|ファイルまたはプロジェクトに追加するディレクトリを指定します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 A`string`テンプレート .zip ファイル内のファイルに名前またはパスを表すです。  
  
## <a name="remarks"></a>コメント  
 `ProjectItem`省略可能な子の`Project`します。  
  
 `TargetFileName`属性は、テンプレートの .zip ファイルのディレクトリ構造からさまざまなディレクトリ構造を作成するために使用できます。 たとえば場合、ファイル`MyFile.vb`テンプレート .zip ファイルのルートに存在するファイルをという名前のディレクトリに配置する必要しますが、`CustomFiles`テンプレートから作成されたすべてのプロジェクトでは、次の XML を使用します。  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`属性は、ファイル名に国際文字を含むファイルの名前を変更するも使用できます。 たとえば、.zip ファイルに圧縮できる前に、ファイル名を変更する必要がありますので、テンプレート .zip ファイルは Unicode 文字を含むファイル名を含めることはできません。 `TargetFileName`属性は、元の Unicode ファイルの名前に戻し、ファイル名の設定を使用することができます。  
  
 `TargetFileName`属性は、パラメーターを持つファイルの名前を変更するも使用できます。 次の手順は、ファイルの名前を変更する方法を説明します。 `MyFile.vb`、プロジェクト名に基づいてファイル名に、テンプレート .zip ファイルのルート ディレクトリに存在します。  
  
### <a name="to-rename-files-with-parameters"></a>パラメーターを持つファイルの名前を変更するには  
  
1.  .Vstemplate ファイルで、次の XML を使用します。  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  プロジェクト ファイルを開きます (の .vbproj、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]プロジェクト) をテキスト エディターでまたは[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
3.  次の XML に類似したプロジェクト ファイル内の行を探します。  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  コードの行を次の XML に置き換えます。  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     ファイル名はで、ユーザーが入力した名前に基づいて、このテンプレートからプロジェクトが作成されると、**新しいプロジェクト**ダイアログ ボックスで、すべての安全でない文字とスペースを削除します。 詳細については、次を参照してください。[テンプレート パラメーター](../ide/template-parameters.md)です。  
  
## <a name="example"></a>例  
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
  
## <a name="see-also"></a>参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)   
 [ProjectItem 要素 (Visual Studio 項目テンプレート)](../extensibility/projectitem-element-visual-studio-item-templates.md)