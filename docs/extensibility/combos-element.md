---
title: "コンボ要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンボ要素 (VSCT XML スキーマ)"
  - "コンボ、VSCT XML スキーマ要素"
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# コンボ要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

複数の [コンボ要素](../extensibility/combo-element.md) 要素をグループ化します。  
  
## 構文  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
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
|[Combos Element](../extensibility/combos-element.md)|コンボ要素をグループ化します。|  
|[コンボ要素](../extensibility/combo-element.md)|コンボ ボックスに表示されるコマンドを定義します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage のツールバーでコマンドのコレクションを表します。|  
  
## 使用例  
  
```  
<Combos> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0500" type="DropDownCombo" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> </Combos>  
```  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)