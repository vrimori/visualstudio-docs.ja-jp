---
title: ProjectItem 要素 (Visual Studio 項目テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51fe9e60bf646e91b957210c43ca020b16f420c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539277"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem 要素 (Visual Studio 項目テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ProjectItem 要素 (Visual Studio 項目テンプレート)](https://docs.microsoft.com/visualstudio/extensibility/projectitem-element-visual-studio-item-templates)します。  
  
項目テンプレートに含まれているファイルを指定します。  
  
> [!NOTE]
>  `ProjectItem`要素には、プロジェクトまたは項目テンプレートは、かどうかに応じてさまざまな属性が使用できます。 このトピックで説明します、`ProjectItem`項目の要素。 詳細については、`ProjectItem`プロジェクトのテンプレートの要素を参照してください[ProjectItem 要素 (Visual Studio プロジェクト テンプレート)](../extensibility/projectitem-element-visual-studio-project-templates.md)します。  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<ProjectItem >  
  
## <a name="syntax"></a>構文  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`SubType`|省略可能な属性です。<br /><br /> 複数ファイルの項目テンプレートでは、アイテムのサブタイプを指定します。 この値は、エディターを使用する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]項目を開くには使用します。|  
|`CustomTool`|省略可能な属性です。<br /><br /> プロジェクト ファイル内の項目の CustomTool を設定します。|  
|`ItemType`|省略可能な属性です。<br /><br /> プロジェクト ファイル内の項目の ItemType を設定します。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> アイテムが、テンプレートからプロジェクトが作成されるときに置き換える必要があるパラメーターの値があるかどうかを指定するブール値。 既定値は `false`にする必要があります。|  
|`TargetFileName`|省略可能な属性です。<br /><br /> テンプレートから作成される項目の名前を指定します。 この属性は、パラメーター置換を使用して、アイテムの名前を作成する場合に便利です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|テンプレートの内容を指定します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 A`string`テンプレート .zip ファイル内のファイルの名前を表します。  
  
## <a name="remarks"></a>Remarks  
 `ProjectItem` 省略可能な子の`TemplateContent`します。  
  
 `TargetFileName`属性を使用して、パラメーターを持つファイルの名前を変更することができます。 たとえば場合、ファイル`MyFile.vb`内のユーザーによって提供されるファイル名に基づいてファイルの名前を指定しますが、テンプレート .zip ファイルのルート ディレクトリに存在する、**新しい項目の追加**ダイアログ ボックスで、次の XML を使用すると。  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 ファイル名はで、ユーザーが入力した名前に基づいて、このテンプレートから項目が作成されると、**新しい項目の追加** ダイアログ ボックス。 これは、機能は、複数ファイルの項目テンプレートを作成するときに便利です。 詳細については、次を参照してください。[方法: 複数ファイル項目テンプレートを作成](../ide/how-to-create-multi-file-item-templates.md)と[テンプレート パラメーター](../ide/template-parameters.md)します。  
  
## <a name="example"></a>例  
 次の例では、用の標準的な項目テンプレートのメタデータを[!INCLUDE[csprcs](../includes/csprcs-md.md)]クラス。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [方法 : 複数ファイルの項目テンプレートを作成する](../ide/how-to-create-multi-file-item-templates.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)

