---
title: "ショートカット キーの要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "KeyBindings"
helpviewer_keywords: 
  - "VSCT XML スキーマ要素のショートカット キー"
  - "ショートカット キーの要素 (VSCT XML スキーマ)"
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# ショートカット キーの要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ショートカット キーの要素には、キーの割り当て要素およびその他のショートカット キーのグループがグループ化します。  
  
## 構文  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
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
|[Keybinding を割り当てる要素](../extensibility/keybinding-element.md)|コマンドのキーボード ショートカットを指定します。|  
|[KeyBindings](../extensibility/keybindings-element.md)|Keybinding を割り当てる要素をグループ化し、その他のショートカット キーのグループ化します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|コマンドを表すすべての要素を定義します。|  
  
## 使用例  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## 参照  
 [Keybinding を割り当てる要素](../extensibility/keybinding-element.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)