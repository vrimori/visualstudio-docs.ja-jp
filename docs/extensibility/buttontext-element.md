---
title: "ButtonText 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ButtonText 要素 (VSCT XML スキーマ)"
  - "ButtonText、VSCT XML スキーマ要素"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# ButtonText 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このフィールドでは、さまざまなメニューに表示されるテキストを指定できます。 既定では、 `ButtonText` \] メニューの \[コント ローラーに要素が表示されます。`ButtonText` 要素は既定値にもなります、他のテキスト フィールドが空白だった場合。`ButtonText` 場合でも、他のテキスト フィールドが指定されている要素を空にすることはできません。  
  
## 構文  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[文字列の要素](../extensibility/strings-element.md)|などのテキスト要素をグループ化 `ButtonText` と `CommandName`です。|  
  
## テキスト値  
 テキスト値、 `ButtonText` 要素がメニュー項目、コンボ、およびその他のユーザー インターフェイス \(UI\) 要素を表示されるテキストを持つに対して表示されるテキストを提供します。  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)