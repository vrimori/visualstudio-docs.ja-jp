---
title: "prototype プロパティ (Map) | Microsoft Docs"
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype プロパティ (Map)
マップのプロトタイプへの参照を返します。  
  
## 構文  
  
```javascript  
map.prototype  
```  
  
## 解説  
 `map` 引数は、マップの名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、`Map` オブジェクトにセット内で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Map.prototype` に追加してから使用します。  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]