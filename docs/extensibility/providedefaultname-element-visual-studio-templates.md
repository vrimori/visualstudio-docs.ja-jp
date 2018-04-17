---
title: ProvideDefaultName 要素 (Visual Studio テンプレート) |Microsoft ドキュメント
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
ms.openlocfilehash: c56ad565dfffd454eeca465aa4097c077fdc0a65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName 要素 (Visual Studio テンプレート)
指定するかどうか、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト システムでテンプレートの既定の名前によって生成されます、**新しい項目の追加**または**新しいプロジェクト** ダイアログ ボックス。  
  
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
  
 テキストはいずれかである必要があります`true`または`false`、内のテンプレートの既定の名前を生成するかどうかを示す、**新しい項目の追加**または**新しいプロジェクト** ダイアログ ボックス。  
  
## <a name="remarks"></a>コメント  
 `ProvideDefaultName` は、省略可能な要素です。 既定値は `true` です。  
  
 場合、`ProvideDefaultName`要素は`false`、**名前**のボックス、**新しい項目の追加**と**新しいプロジェクト** ダイアログ ボックスに値が含まれて`<Enter_name>`です。  
  
 使用して、 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)要素プロジェクトの既定の名前を指定するか、内の項目を**新しい項目の追加**と**新しいプロジェクト** ダイアログ ボックス。  
  
## <a name="example"></a>例  
 次のコード例のセット、`ProvideDefaultName`要素を`false`です。  
  
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