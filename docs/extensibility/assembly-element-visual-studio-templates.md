---
title: Assembly 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74e57ae61ddfaa24de4cc8e3e332b3fa9f7250c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912900"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly 要素 (Visual Studio テンプレート)
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
  
## <a name="attributes-and-elements"></a>属性と要素  
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
  
-   アセンブリの完全名。 例:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   単純なテキストの参照。 例:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## <a name="remarks"></a>Remarks  
 `Assembly` は `Reference` に必須の子要素です。  
  
 `Reference`、`References,`と`Assembly`要素でのみ使用できます *.vstemplate*を持つファイルを`Type`属性の値`Item`します。  
  
## <a name="example"></a>例  
 次の例を示しています、`TemplateContent`項目テンプレートの要素。 この XML への参照の追加、 *System.dll*と*System.Data.dll*アセンブリ。  
  
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
 [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)