---
title: "Groups 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "グループ、VSCT XML スキーマ要素"
  - "Groups 要素 (VSCT XML スキーマ)"
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Groups 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage のコマンド グループを定義するエントリが含まれています。  
  
## 構文  
  
```  
<Groups>  
  <Group>... </Group>  
  <Group>... </Group>  
</Groups>  
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
|[Group 要素](../extensibility/group-element.md)|1 つのコマンド グループを表します。|  
|[Groups Element](../extensibility/groups-element.md)|VSPackage のコマンド グループを定義するエントリが含まれています。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage のツールバーでコマンドのコレクションを表します。|  
  
## 使用例  
  
```  
<Groups> <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group> </Groups>  
```  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)