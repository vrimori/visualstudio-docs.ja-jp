---
title: "prototype プロパティ (Intl.DateTimeFormat) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype プロパティ (Intl.DateTimeFormat)
フォーマッタのプロトタイプへの参照を返します。  
  
## 構文  
  
```javascript  
dateTimeFormat.prototype  
```  
  
## 解説  
 `dateTimeFormat` 引数は、フォーマッタの名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、`Intl.DateTimeFormat` オブジェクトにセット内で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Intl.DateTimeFormat.prototype` に追加してから使用します。  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]