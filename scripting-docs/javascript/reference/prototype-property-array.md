---
title: "prototype プロパティ (配列) | Microsoft Docs"
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype プロパティ (配列)
指定された配列のクラスのプロトタイプへの参照を返します。  
  
## 構文  
  
```  
  
array.prototype  
```  
  
## 解説  
 `array` 引数は配列の名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの動作を "継承" します。  
  
 たとえば、`Array` オブジェクトに配列内で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Array.prototype` に追加してから使用します。  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 組み込み [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトはすべて、値の取得のみ可能な `prototype` プロパティを持っています。  プロパティとメソッドはプロトタイプに追加できますが、オブジェクトを別のプロトタイプに割り当てることはできません。  ただし、ユーザー定義オブジェクトは、新しいプロトタイプに割り当てることができます。  
  
 この言語リファレンスには、組み込みオブジェクトごとにメソッドとプロパティの一覧があり、オブジェクトのプロトタイプに含まれているメソッドとプロパティを調べることができます。  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]