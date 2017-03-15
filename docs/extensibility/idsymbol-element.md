---
title: "IDSymbol 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDSymbol 要素 (VSCT XML スキーマ)"
  - "IDSymbol、VSCT XML スキーマ要素"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDSymbol 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`IDSymbol` 要素には、メニューのグループ、またはコマンドを表す GUID:ID ペアの ID が含まれています。 GUID は、親から `GuidSymbol` 要素。`IDSymbol` 要素には、 `name` 属性に含まれている ID のフレンドリ名を提供する、 `value` 属性です。  
  
## 構文  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|name|必須です。 ID シンボルの名前です。|  
|値|必須です。 ID シンボルの数値の ID 値です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[GuidSymbol 要素](../extensibility/guidsymbol-element.md)|メニューのグループ、またはコマンドを表す GUID:ID ペアの GUID が含まれています。 複数の `IDSymbol` 要素をグループ化します。|  
  
## 解説  
 すべて `IDSymbol` 内の要素を指定した `GuidSymbol` 要素の一意な名前が `value`です。 ただし、 `IDSymbol` と同じ値を持つ要素は、別の親を持っていれば、パッケージに存在できます。  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)