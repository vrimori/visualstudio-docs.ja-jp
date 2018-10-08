---
title: SortOrder 要素 (Visual Studio テンプレート) |Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4619d151e66d288907dea97894a1ae133be8708b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544336"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SortOrder 要素 (Visual Studio テンプレート)](https://docs.microsoft.com/visualstudio/extensibility/sortorder-element-visual-studio-templates)します。  
  
いずれかに表示される、同じカテゴリ内の他のテンプレート間で、テンプレートの配置に使用する値を指定します、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SortOrder >  
  
## <a name="syntax"></a>構文  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 `integer`並べ替え順序の値を表します。  
  
## <a name="remarks"></a>Remarks  
 `SortOrder` は、省略可能な要素です。 既定値は 100、およびすべての値は 10 の倍数である必要があります。  
  
 `SortOrder`ユーザーが作成したテンプレートの要素は無視されます。 すべてのユーザーが作成したテンプレートは、アルファベット順に並べ替えられます。  
  
 いずれかで、低の並べ替え順序の値を持つテンプレートが表示されます、**新しいプロジェクト**または**新しい項目の追加**高の並べ替え順序の値を持つテンプレートの前に ダイアログ ボックス。  
  
## <a name="example"></a>例  
 次の例では、標準のメタデータ[!INCLUDE[csprcs](../includes/csprcs-md.md)]クラス テンプレートです。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 この例で、`SortOrder`要素が比較的高い。 可能性がありますの他の[!INCLUDE[csprcs](../includes/csprcs-md.md)]項目テンプレートには、`SortOrder`よりも小さい値`290`と前にこのテンプレートに表示されます、**新しい項目の** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)

