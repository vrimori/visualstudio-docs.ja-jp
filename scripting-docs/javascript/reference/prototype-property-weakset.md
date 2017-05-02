---
title: "prototype プロパティ (WeakSet) | Microsoft Docs"
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype プロパティ (WeakSet)
`WeakSet` のプロトタイプへの参照を返します。  
  
## 構文  
  
```javascript  
weakset.prototype  
```  
  
## 解説  
 `weakset` 引数は、セットの名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、`WeakSet` オブジェクトにセット内で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `WeakSet.prototype` に追加してから使用します。  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]