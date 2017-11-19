---
title: "MaxFrameworkVersion 要素 (Visual Studio テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da1b30274254c5c1dd81ad20dd64e8749672f96e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 要素 (Visual Studio テンプレート)
テンプレートで必要とされる .NET Framework の最大バージョンを指定します。 テンプレートが表示されるかどうかを判定、**テンプレート**のセクションで、**新しいプロジェクトの追加**で選択されている値に基づいて、ダイアログ ボックス、 **ターゲットフレームワークのバージョン**のボックス、**新しいプロジェクトの追加** ダイアログ ボックス。  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>構文  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必須の要素です。<br /><br /> テンプレートをカテゴリに分類し、いずれかでの表示方法を定義、**新しいプロジェクト**または**新しい項目の追加** ダイアログ ボックス。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 テキストは、テンプレートで許可されている .NET Framework の最新のバージョン番号があります。  
  
## <a name="remarks"></a>コメント  
 `MaxFrameworkVersion` は、省略可能な要素です。 内の要素、 `TemplateData` .vstemplate ファイルのセクションでは、のフィルターとして機能、**テンプレート**のセクションで、**新しいプロジェクトの追加** ダイアログ ボックス。 .NET Framework の要件は次のテンプレートのみより小さい`MaxFrameworkVersion`要素の値が表示されますで選択されている値に基づいて、**ターゲット フレームワークのバージョン**のボックス、**新しいプロジェクトの追加** ダイアログ ボックス。 `MaxFrameworkVersion`から .NET Framework の新しいバージョンで使用している場合に表示されているテンプレートを誤って原因にならないように、必要である場合を除き、要素を省略する必要があります。  
  
## <a name="example"></a>例  
 次の例では、標準のメタデータ[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]クラス テンプレートです。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 この例では、テンプレートで必要とされる .NET Framework の最大バージョンによって表される`MaxFrameworkVersion`、3.5。 3.0 または 3.5 インチのいずれかを選択する場合にのみ、上記のテンプレートが表示されます、**ターゲット フレームワークのバージョン**ボックスに、**新しいプロジェクトの追加** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)