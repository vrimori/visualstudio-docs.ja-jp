---
title: "ビットマップ要素 | Microsoft Docs"
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
  - "ビットマップ、VSCT XML スキーマ要素"
  - "ビットマップ要素 (VSCT XML スキーマ)"
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# ビットマップ要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

複数の [ビットマップ要素](../extensibility/bitmap-element.md) 要素をグループ化します。  
  
## 構文  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
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
|[Bitmaps Element](../extensibility/bitmaps-element.md)|ビットマップの要素をグループ化します。|  
|[ビットマップ要素](../extensibility/bitmap-element.md)|ビットマップを定義します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[Commands 要素](../extensibility/commands-element.md)|VSPackage のツールバーでコマンドのコレクションを表します。|  
  
## 使用例  
  
```  
<Bitmaps> <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/> </Bitmaps>  
```  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)