---
title: "Group 要素 | Microsoft Docs"
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
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Group 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage コマンド グループを定義します。  
  
## 構文  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。 GUID と ID コマンドの識別子の GUID です。|  
|ID|必須です。 GUID と ID コマンドの識別子の ID です。|  
|priority|省略可能です。 優先順位を指定する数値。|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|親|省略可能です。 ボタンの親要素です。|  
|注釈|省略可能なコメントです。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Groups 要素](../extensibility/groups-element.md)|VSPackage のコマンド グループを定義するエントリが含まれています。|  
  
## 使用例  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)