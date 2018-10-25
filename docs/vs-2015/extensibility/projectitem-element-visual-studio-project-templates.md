---
title: ProjectItem 要素 (Visual Studio プロジェクト テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16caf0ec50d061a1f7e89aa5bee141495397ce68
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301302"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 要素 (Visual Studio プロジェクト テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プロジェクト テンプレートに含まれているファイルを指定します。  
  
> [!NOTE]
>  `ProjectItem`要素には、プロジェクトまたは項目テンプレートは、かどうかに応じてさまざまな属性が使用できます。 このトピックで説明します、`ProjectItem`プロジェクト テンプレートの要素。 詳細については、`ProjectItem`項目テンプレートの要素を参照してください[ProjectItem 要素 (Visual Studio 項目テンプレート)](../extensibility/projectitem-element-visual-studio-item-templates.md)します。  
  
 \<VSTemplate>  
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
|`TargetFileName`|省略可能な属性です。<br /><br /> テンプレートからプロジェクトが作成されたときに、プロジェクト項目のパスと名前を指定します。 この属性は、テンプレート .zip ファイル、ディレクトリ構造からさまざまなディレクトリ構造を作成するためや、パラメーター置換を使用して、アイテムの名前を作成するのに便利です。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> アイテムが、テンプレートからプロジェクトが作成されるときに置き換える必要があるパラメーターの値があるかどうかを指定するブール値。 既定値は `false`にする必要があります。|  
|`OpenInEditor`|省略可能な属性です。<br /><br /> それぞれのエディターで、項目を開く必要があるかどうかを指定するブール値[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]テンプレートからプロジェクトを作成する時。<br /><br /> `OpenInWebBrowser`と`OpenInHelpBrowser`を持つ項目の属性は無視されます、 `OpenInEditor` @property`true`します。<br /><br /> 既定値は `false` です。|  
|`OpenInWebBrowser`|省略可能な属性です。<br /><br /> かどうか、項目開く必要があります、Web ブラウザー、テンプレートからプロジェクトが作成されるときを示すブール値。<br /><br /> Web ブラウザーでは、HTML ファイルとは、プロジェクトにローカル テキスト ファイルだけを開くことができます。 この属性では、外部 Url を開くことができません。<br /><br /> 既定値は `false` です。|  
|`OpenInHelpBrowser`|省略可能な属性です。<br /><br /> テンプレートからプロジェクトが作成されたときに、アイテムをヘルプ ビューアーで開く必要があるかどうかを指定するブール値。<br /><br /> HTML ファイルとは、プロジェクトにローカル テキスト ファイルだけは、ヘルプ ブラウザーで開くことができます。 この属性では、外部 Url を開くことができません。<br /><br /> 既定値は `false` です。|  
|`OpenOrder`|省略可能な属性です。<br /><br /> 項目が、それぞれのエディターで開かれることの順序を表す数値を指定します。 すべての値は 10 の倍数である必要があります。 以上の項目`OpenOrder`値が最初に開かれます。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[プロジェクト](../extensibility/project-element-visual-studio-templates.md)|ファイルまたはプロジェクトに追加するディレクトリを指定します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 A`string`名前またはパスをテンプレート .zip ファイル内のファイルを表します。  
  
## <a name="remarks"></a>Remarks  
 `ProjectItem` 省略可能な子の`Project`します。  
  
 `TargetFileName`属性を使用して、テンプレートの .zip ファイルのディレクトリ構造からさまざまなディレクトリ構造を作成することができます。 たとえば場合、ファイル`MyFile.vb`、テンプレート .zip ファイルのルートに存在するという名前のディレクトリに配置すること、ファイルしますが、`CustomFiles`テンプレートから作成されたすべてのプロジェクトでは、次の XML を使用します。  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`属性がファイル名に国際文字を含むファイルの名前を変更することもできます。 たとえば、テンプレート .zip ファイルは .zip ファイルに圧縮する前に、ファイルの名前を変更する必要がありますので文字を Unicode ファイル名を含めることはできません。 `TargetFileName`属性を使用して、ファイル名を元の Unicode ファイル名に設定することができます。  
  
 `TargetFileName`属性がパラメーターを持つファイルの名前を変更することもできます。 次の手順は、ファイルの名前を変更する方法を説明します。 `MyFile.vb`、プロジェクト名に基づいてファイル名に、テンプレート .zip ファイルのルート ディレクトリに存在します。  
  
### <a name="to-rename-files-with-parameters"></a>パラメーターを持つファイルの名前を変更するには  
  
1.  .Vstemplate ファイルでは、次の XML を使用します。  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  プロジェクト ファイルを開きます (の .vbproj、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]プロジェクト) をテキスト エディターでまたは[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。  
  
3.  次の xml のようなプロジェクト ファイル内の行を見つけます。  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  コード行を次の XML に置き換えます。  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     ファイル名はで、ユーザーが入力した名前に基づいて、このテンプレートからプロジェクトが作成されると、**新しいプロジェクト** ダイアログ ボックスのすべての安全でない文字とスペースを削除します。 詳細については、次を参照してください。[テンプレート パラメーター](../ide/template-parameters.md)します。  
  
## <a name="example"></a>例  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] アプリケーションでのプロジェクト テンプレートのメタデータの例を次に示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)   
 [ProjectItem 要素 (Visual Studio 項目テンプレート)](../extensibility/projectitem-element-visual-studio-item-templates.md)

