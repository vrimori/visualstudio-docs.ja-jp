---
title: ProvideDefaultName 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a187df0e50a2948ab6f1ef3a0fffea651dca23b9
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636013"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName 要素 (Visual Studio テンプレート)
指定するかどうか、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト システムの既定のテンプレートの名前が生成されます、**新しい項目の追加**または**新しいプロジェクト** ダイアログ ボックス。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProvideDefaultName >  
  
## <a name="syntax"></a>構文  
  
```xml  
<ProvideDefaultName> true/false </ProvideDefaultName>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 テキストがいずれかにする必要があります`true`または`false`の既定のテンプレートの名前を生成するかどうかを示す、**新しい項目の追加**または**新しいプロジェクト** ダイアログ ボックス。  
  
## <a name="remarks"></a>Remarks  
 `ProvideDefaultName` は、省略可能な要素です。 既定値は `true` です。  
  
 場合、`ProvideDefaultName`要素は`false`、**名前**のボックス、**新しい項目の追加**と**新しいプロジェクト** ダイアログ ボックスに値が含まれて`<Enter_name>`します。  
  
 使用して、 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)要素内の項目をプロジェクトの既定の名前を指定または、**新しい項目の追加**と**新しいプロジェクト** ダイアログ ボックス。 ときの値、`ProvideDefaultName`要素は`true`の省略、`DefaultName`要素のプロジェクト テンプレートの名前、値は、ダイアログ ボックスに追加、[名前](../extensibility/name-element-visual-studio-templates.md)要素。
  
## <a name="example"></a>例  
 次のコード例のセット、`ProvideDefaultName`要素`false`します。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
