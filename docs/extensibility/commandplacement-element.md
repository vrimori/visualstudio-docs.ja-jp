---
title: "CommandPlacement 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommandPlacements 要素 (VSCT XML スキーマ)"
  - "CommandPlacements、VSCT XML スキーマ要素"
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# CommandPlacement 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CommandPlacement 要素は、1 つ以上のグループまたはメニューに含まれるには、ボタン、グループ、およびメニューを使用します。 CommandPlacement 要素を使用すると、ユーザー インターフェイスの外観を変更するために、これらの項目を完全に再定義する必要はありません。  
  
 詳細については、「[ボタンの再利用可能なグループを作成します。](../extensibility/creating-reusable-groups-of-buttons.md)」を参照してください。  
  
## 構文  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。 定義されている、コマンド セットの guid、 [シンボル要素](../extensibility/symbols-element.md)です。|  
|ID|必須です。 メニューのグループ、または配置するで定義されているコマンドの id、 `Symbols Element`です。|  
|priority|必須です。 その親要素内のアイテムの位置を visual を決定します。|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|親|必須です。 メニューまたはグループを配置する項目をホストしています。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CommandPlacements 要素](../extensibility/commandplacements-element.md)|CommandPlacements および CommandPlacement 要素のグループを指定します。|  
  
## 使用例  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## 参照  
 [CommandPlacements 要素](../extensibility/commandplacements-element.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)