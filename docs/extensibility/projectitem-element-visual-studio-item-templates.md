---
title: "ProjectItem 要素 (Visual Studio 項目テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2fe9abece45efdc206e775bc8f5e79666e334001
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem 要素 (Visual Studio 項目テンプレート)
項目テンプレートに含まれているファイルを指定します。  
  
> [!NOTE]
>  `ProjectItem`要素は、テンプレートが、プロジェクトまたは項目があるかによって異なる属性を受け入れます。 このトピックの内容について説明します、`ProjectItem`項目の要素。 詳細について、`ProjectItem`プロジェクト テンプレートの要素を参照してください[ProjectItem 要素 (Visual Studio プロジェクト テンプレート)](../extensibility/projectitem-element-visual-studio-project-templates.md)です。  
  
 \<VSTemplate >  
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
|`SubType`|省略可能な属性です。<br /><br /> 複数ファイルの項目テンプレートのアイテムのサブタイプを指定します。 この値は、エディターの決定に使用する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]アイテムを開いてから使用されます。|  
|`CustomTool`|省略可能な属性です。<br /><br /> プロジェクト ファイルで、項目の CustomTool を設定します。|  
|`ItemType`|省略可能な属性です。<br /><br /> プロジェクト ファイルで、項目の ItemType を設定します。|  
|`ReplaceParameters`|省略可能な属性です。<br /><br /> アイテムが、テンプレートからプロジェクトの作成時に置き換える必要があるパラメーターの値があるかどうかを指定するブール値。 既定値は `false`にする必要があります。|  
|`TargetFileName`|省略可能な属性です。<br /><br /> テンプレートから作成された項目の名前を指定します。 この属性は、パラメーター置換を使用して、アイテムの名前を作成するのに役立ちます。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|テンプレートの内容を指定します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 A`string`テンプレート .zip ファイル内のファイルの名前を表します。  
  
## <a name="remarks"></a>コメント  
 `ProjectItem`省略可能な子の`TemplateContent`します。  
  
 `TargetFileName`パラメーターを持つファイルの名前を変更する属性を使用できます。 たとえば場合、ファイル`MyFile.vb`する名前を指定するファイル名を基に、ファイル内のユーザーによって提供されるテンプレート .zip ファイルのルート ディレクトリに存在する、**新しい項目の追加**ダイアログ ボックスで、次の XML を使用すると。  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 ファイル名はで、ユーザーが入力した名前に基づいて、項目がこのテンプレートから作成されると、**新しい項目の追加** ダイアログ ボックス。 これは、機能は、複数ファイルの項目テンプレートを作成するときに便利です。 詳細については、次を参照してください。[する方法: 複数ファイルの項目テンプレートを作成する](../ide/how-to-create-multi-file-item-templates.md)と[テンプレート パラメーター](../ide/template-parameters.md)です。  
  
## <a name="example"></a>例  
 次の例では、メタデータの標準項目テンプレートを[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]クラスです。  
  
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
  
## <a name="see-also"></a>参照  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [方法 : 複数ファイルの項目テンプレートを作成する](../ide/how-to-create-multi-file-item-templates.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)