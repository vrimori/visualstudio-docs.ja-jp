---
title: ProvideDefaultName 要素 (Visual Studio テンプレート) |Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c97fdb245ba1ff066e19bcd32616649b47b9425
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533662"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ProvideDefaultName 要素 (Visual Studio テンプレート)](https://docs.microsoft.com/visualstudio/extensibility/providedefaultname-element-visual-studio-templates)します。  
  
指定するかどうか、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト システムの既定のテンプレートの名前が生成されます、**新しい項目の追加**または**新しいプロジェクト** ダイアログ ボックス。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProvideDefaultName >  
  
## <a name="syntax"></a>構文  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
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
  
 使用して、 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)要素内の項目をプロジェクトの既定の名前を指定または、**新しい項目の追加**と**新しいプロジェクト** ダイアログ ボックス。  
  
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
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)

