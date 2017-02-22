---
title: "ボタン要素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ボタン要素 (VSCT XML スキーマ)"
  - "ボタン、VSCT XML スキーマ要素"
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ボタン要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グループ [ボタン](../extensibility/button-element.md) 要素で、個々 のコマンドを表します。  
  
## 構文  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
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
|[Buttons Element](../extensibility/buttons-element.md)|ボタン要素をグループ化します。|  
|[Button 要素](../extensibility/button-element.md)|ユーザーが対話できるコマンドを定義します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage のツールバーでコマンドのコレクションを表します。|  
  
## 使用例  
  
```  
<Buttons> <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button"> <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/> <Icon guid="guidGenericCmdBmp" id="bmpArrow"/> <Strings> <ButtonText>C# Command Sample</ButtonText> </Strings> </Button> </Buttons>  
```  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)