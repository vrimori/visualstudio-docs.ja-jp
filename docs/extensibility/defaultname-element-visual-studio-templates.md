---
title: "DefaultName 要素 (Visual Studio テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords: DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6a20bd878e9c6f85e03ff0738ed2a92d274f6232
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName 要素 (Visual Studio テンプレート)
作成時に、プロジェクトまたはアイテムの Visual Studio プロジェクト システムが生成される名前を指定します。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<DefaultName >  
  
## <a name="syntax"></a>構文  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 このテキストは、プロジェクトまたは項目の既定の名前を指定します。  
  
## <a name="remarks"></a>コメント  
 `DefaultName` は、省略可能な要素です。  
  
 プロジェクトの場合は、この要素は、ディスク上、プロジェクトを格納するディレクトリの名前を指定します。 アイテムのソース ファイルのファイル名を示します。  
  
 既定値を使用して名前を変更するには、プロジェクトまたは項目を作成するときに、**名前**はいずれかから使用可能なオプション、**新しいプロジェクト** ダイアログ ボックスまたは**新しい項目の追加**ダイアログ ボックス。  
  
 プロジェクトまたは項目の既定の名前を生成するようにプロジェクト システムしたくない場合は、設定、 [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)要素を`False`です。  
  
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