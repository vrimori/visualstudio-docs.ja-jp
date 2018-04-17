---
title: TemplateData 要素 (Visual Studio テンプレート) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbf5b4c26b46c0be6038651a41c751afc39e4da5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 要素 (Visual Studio テンプレート)
テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。  
  
 \<VSTemplate>  
 \<TemplateData>  
  
## <a name="syntax"></a>構文  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|必須の要素です。<br /><br /> いずれかで表示されるテンプレートの名前を指定、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|  
|[説明](../extensibility/description-element-visual-studio-templates.md)|必須の要素です。<br /><br /> いずれかで表示されるテンプレートの説明を指定、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|  
|[アイコン](../extensibility/icon-element-visual-studio-templates.md)|必須の要素です。<br /><br /> パスと、いずれかで表示されるアイコンとして使用するイメージ ファイルのファイル名を指定します、**新しいプロジェクト**または**新しい項目の追加**テンプレートのダイアログ ボックス。|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|必須の要素です。<br /><br /> 指定されたグループの下に表示されるように、プロジェクト テンプレートをカテゴリに分類、**新しいプロジェクト** ダイアログ ボックス。|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 指定したサブカテゴリに表示されるように、プロジェクト テンプレートの分類、**新しいプロジェクト** ダイアログ ボックス。|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> テンプレート ID を指定します|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> テンプレートのグループ ID を指定します|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> いずれかに表示される、同じカテゴリ内のテンプレートのテンプレートの配置に使用する値を示す、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> プロジェクトのインスタンス化時に含まれているフォルダーを作成するかどうかを指定します。|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 作成時に、プロジェクトまたはアイテムの Visual Studio プロジェクト システムが生成される名前を指定します。|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 作成されるときに、Visual Studio プロジェクト システムがプロジェクトまたは項目の既定の名前を生成するかどうかを指定します。|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 一時プロジェクトとして、プロジェクトを作成できるかどうかを指定します。|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 指定するかどうか、**参照**でボタンは使用、**新しいプロジェクト** ダイアログ ボックスで、新しいプロジェクトが保存されている既定のディレクトリを簡単に変更できるようにします。|  
|[非表示](../extensibility/hidden-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> いずれかで、テンプレートを表示するかどうかを指定、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 親カテゴリ内のテンプレートを表示する数を指定します、**新しいプロジェクト** ダイアログ ボックス。|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|省略可能な要素です。|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|省略可能な要素です。<br /><br /> 指定するかどうか、**場所**テキスト ボックスに、**新しいプロジェクト** ダイアログ ボックスが有効になっている、無効になっている、またはプロジェクト テンプレートの非表示になります。|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 特定の最小バージョンと、.NET Framework の以降のバージョンにのみテンプレートがサポートする場合は、この要素を使用します。|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> Web プロジェクトのテンプレートがマスター ページをサポートするかどうかを指定します。|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 指定 web プロジェクトに対して、テンプレートがコード分離付きまたは分離コード ページ モデルをサポートするかどうか。|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> テンプレートが複数の言語と同じかどうかとするかどうかを指定します、**言語**オプションはから利用可能な**新しいプロジェクト** ダイアログ ボックス。|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> プロジェクト テンプレートの対象となるプラットフォームを指定します。 この要素は指定のプロジェクト テンプレートが作成するために使用[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]アプリ。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必須の要素です。<br /><br /> プロジェクト テンプレート、項目テンプレート、またはスタート キットのすべてのメタデータが含まれています。|  
  
## <a name="remarks"></a>コメント  
 `TemplateData` 必要な要素です。  
  
 省略可能な要素を指定しない場合は、その要素の既定値が使用されます。  
  
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
            <ProjectItem>Form1.cs<ProjectItem>  
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