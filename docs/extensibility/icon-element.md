---
title: "Icon 要素 | Microsoft Docs"
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
  - "VSCT XML スキーマ要素のアイコン"
  - "Icon 要素 (VSCT XML スキーマ)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Icon 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アイコンのタグの guid 属性は、定義されているビットマップの guid です。  Id 属性は、ビットマップ ストリップのスロットを選択します。 この要素は省略可能です。  この要素を省略した場合の値 **guidOfficeIcon:msotcidNoIcon** 暗黙的に指定されます。  
  
## 構文  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。 定義済みのビットマップの guid です。|  
|ID|必須です。 ビットマップ ストリップのスロットを選択します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|なし。|なし。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[ボタン要素](../extensibility/buttons-element.md)||  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)