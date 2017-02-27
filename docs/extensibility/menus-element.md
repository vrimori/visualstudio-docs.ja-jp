---
title: "メニュー要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メニュー、VSCT XML スキーマ要素"
  - "メニュー要素 (VSCT XML スキーマ)"
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# メニュー要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

すべてのメニューとツールバー、VSPackage を実装するを定義します。  
  
## 構文  
  
```  
<Menus>  
  <Menu>... </Menu>  
  <Menu>... </Menu>  
</Menus>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[Menus Element](../extensibility/menus-element.md)|すべてのメニューとツールバー、VSPackage を実装するを定義します。|  
|[Menu 要素](../extensibility/menu-element.md)|1 つのメニューまたはツールバーを表します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage でのコマンドのコレクションを表します。|  
  
## 使用例  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)