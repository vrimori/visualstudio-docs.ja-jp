---
title: "CustomParameter 要素 (Visual Studio テンプレート) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters 要素 [Visual Studio プロジェクト テンプレート]"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# CustomParameter 要素 (Visual Studio テンプレート)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テンプレートからプロジェクトまたはアイテムを作成するときに使用する、カスタムのパラメーター名およびパラメーター値を含みます。  
  
## 構文  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`Name`|必須。  パラメーターの名前。  パラメーターの書式は $*name*$ となります。|  
|`Value`|必須。  パラメーターの置換値です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|ウィザードがパラメーターの置換を実行するときにテンプレート ウィザードに渡される、カスタム パラメーターをグループ化します。|  
  
## 解説  
 テンプレートに `CustomParameter` 要素がある場合、作成されたプロジェクト ファイルまたはアイテム ファイル内で、`Name` 属性が `Value` 属性に置き換えられます。  
  
## 使用例  
 テンプレートでカスタム パラメーターを使用する方法を次に示します。  次のカスタム パラメーターを使用してテンプレートからプロジェクトまたはアイテムが作成されると、テンプレート ファイル内のすべての `$color1$` が `Red` に、すべての `$color2$` が `Blue` に置換されます。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## 参照  
 [CustomParameters 要素 \(Visual Studio テンプレート\)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [テンプレート名](../ide/template-parameters.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)