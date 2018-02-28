---
title: "CustomParameter 要素 (Visual Studio テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8b2380a585b1c428516e1578587c64b93d5b1d4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter 要素 (Visual Studio テンプレート)
カスタム パラメーターの名前と、テンプレートからプロジェクトまたは項目を作成するときに使用する値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 パラメーターの名前。 パラメーターの形式は $*名前*$ です。|  
|`Value`|必須。 パラメーターの置換値。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|ウィザードを使用するパラメーターの置換時に、テンプレート ウィザードに渡すカスタム パラメーターをグループ化します。|  
  
## <a name="remarks"></a>コメント  
 テンプレートが含まれている場合`CustomParameter`要素、すべてのインスタンス、`Name`属性に置き換え、`Value`作成したプロジェクトまたはアイテムのファイル内の属性です。  
  
## <a name="example"></a>例  
 次の例では、テンプレートでいくつかのカスタム パラメーターを使用する方法を示します。 次のカスタム パラメーターのすべてのインスタンスを持つテンプレートからプロジェクトまたは項目を作成するときに`$color1$`と`$color2$`テンプレートのファイルが置き換えられます`Red`と`Blue`、それぞれします。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>参照  
 [CustomParameters 要素 (Visual Studio テンプレート)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)