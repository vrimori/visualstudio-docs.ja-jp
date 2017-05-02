---
title: "prototype プロパティ (日付) | Microsoft Docs"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype プロパティ (日付)
日付のプロトタイプへの参照を返します。  
  
## 構文  
  
```  
  
date.prototype  
```  
  
## 解説  
 `date` 引数はオブジェクトの名前です。  
  
 `prototype` プロパティを使用すると、Date が持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの動作を "継承" します。  
  
 たとえば、`Date` オブジェクトに配列内で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Date.prototype` に追加してから使用します。  
  
```javascript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 組み込み [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトはすべて、値の取得のみ可能な `prototype` プロパティを持っています。  プロパティとメソッドはプロトタイプに追加できますが、オブジェクトを別のプロトタイプに割り当てることはできません。  ただし、ユーザー定義オブジェクトは、新しいプロトタイプに割り当てることができます。  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]