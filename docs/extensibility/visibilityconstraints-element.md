---
title: "VisibilityConstraints 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisibilityConstraints"
helpviewer_keywords: 
  - "VisibilityConstraints、VSCT XML スキーマ要素"
  - "VisibilityConstraints 要素 (VSCT XML スキーマ)"
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# VisibilityConstraints 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VisibilityConstraints 要素では、コマンドとツールバーのグループの静的な可視性を決定します。 可視性は、まずによって制御、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage を読み込むことがなく、統合開発環境 \(IDE\) です。  
  
## 構文  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
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
|[VisibilityItem 要素](../extensibility/visibilityitem-element.md)|コマンドとツールバーの静的な可視性を決定します。|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|コマンドとツールバーのグループの静的な可視性を決定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[CommandTable 要素](../extensibility/commandtable-element.md)|VSPackage を IDE に提供するコマンド \(たとえば、メニュー項目、メニューのツールバー、およびコンボ ボックスなど\) を表すすべての要素を定義します。|  
  
## 使用例  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## 参照  
 [VisibilityItem 要素](../extensibility/visibilityitem-element.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)