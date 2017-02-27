---
title: "GuidSymbol 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GuidSymbol、VSCT XML スキーマ要素"
  - "GuidSymbol 要素 (VSCT XML スキーマ)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# GuidSymbol 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`GuidSymbol` 要素には、メニューのグループ、またはコマンドを表す GUID:ID ペアの GUID が含まれています。 ID に由来する `IDSymbol` 内の要素、 `GuidSymbol` 要素。`GuidSymbol` 要素には、 `name` 属性に含まれている GUID のフレンドリ名を提供する、 `value` 属性です。  
  
## 構文  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|name|必須です。 GUID 記号の名前です。|  
|値|必須です。 GUID 記号の GUID です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[IDSymbol 要素](../extensibility/idsymbol-element.md)|メニューのグループ、またはコマンドを表す GUID:ID ペアの ID が含まれています。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[シンボル要素](../extensibility/symbols-element.md)|グループ `GuidSymbol` .vsct ファイル内の要素。|  
  
## 解説  
 通常、.vsct ファイルには、3 つの `GuidSymbol` 内の要素の `Symbols` 」で、パッケージ自体、コマンド セット \(メニューのグループ、およびパッケージが利用できるようにするコマンドのコレクション\) のいずれかと、ビットマップのボタンやその他のビジュアル コンポーネントのアイコンを提供する 1 つのいずれかです。 すべて `IDSymbol` 内の要素を指定した `GuidSymbol` 要素の一意な名前が `value`です。ただし、 `IDSymbol` と同じ値を持つ要素は、別の親を持っていれば、パッケージに存在できます。  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)