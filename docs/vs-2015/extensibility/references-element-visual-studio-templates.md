---
title: 要素 (Visual Studio テンプレート) を参照 |Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c385e895480ed11b480c1d5d1e4085d71952e4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202950"
---
# <a name="references-element-visual-studio-templates"></a>References 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このテンプレートはプロジェクトに追加するアセンブリ参照をグループ化します。  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<参照 >  
  
## <a name="syntax"></a>構文  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[参照](../extensibility/reference-element-visual-studio-templates.md)|必須の要素です。<br /><br /> 項目がプロジェクトに追加されたときに追加するアセンブリ参照を指定します。 1 つまたは複数がある必要があります`Reference`内の要素を`References`要素。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|テンプレートの内容を指定します。|  
  
## <a name="remarks"></a>Remarks  
 `References` は、`TemplateContent` の子要素で、省略可能な要素です。  
  
 `Reference`と`References`要素は、.vstemplate ファイルでのみ使用できます、`Type`属性の値`Item`します。  
  
## <a name="example"></a>例  
 次の例を示しています、`TemplateContent`項目テンプレートの要素。 この XML は、System.dll および System.Data.dll アセンブリへの参照を追加します。  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)

