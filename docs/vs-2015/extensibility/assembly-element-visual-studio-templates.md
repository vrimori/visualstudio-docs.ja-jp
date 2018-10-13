---
title: Assembly 要素 (Visual Studio テンプレート) |Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd0a03d78e00c5c075ae3654b08912f151ec7cc9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237758"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

そのアセンブリの参照をプロジェクトに追加するテンプレートを使用して、アセンブリに関する情報を指定します。  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<参照 >  
 \<参照 >  
 \<アセンブリ >  
  
## <a name="syntax"></a>構文  
  
```  
<Assembly> AssemblyName </Assembly>  
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
|[参照](../extensibility/reference-element-visual-studio-templates.md)|項目がプロジェクトに追加されたときに追加するアセンブリ参照を指定します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 このテキストは、項目テンプレートがインスタンス化されるときに、プロジェクトに追加するアセンブリを指定します。 このアセンブリの名前は、次の方法のいずれかで指定する必要があります。  
  
-   アセンブリの完全名。 例えば:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   単純なテキストの参照。 例えば:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Remarks  
 `Assembly` は `Reference` に必須の子要素です。  
  
 `Reference`、`References,`と`Assembly`要素は、.vstemplate ファイルでのみ使用できます、`Type`属性の値`Item`します。  
  
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

