---
title: "prototype プロパティ (数値) | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype プロパティ (数値)
指定された数値のクラスのプロトタイプへの参照を返します。  
  
## 構文  
  
```  
  
number.prototype  
```  
  
## 解説  
 `number` 引数は、数値の名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの動作を "継承" します。  
  
 たとえば、`Number` オブジェクトに桁数 \(整数\) を返すメソッドを追加する場合は、関数を宣言して `Number.prototype` に追加してから使用します。  
  
```javascript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 組み込み [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトはすべて、値の取得のみ可能な `prototype` プロパティを持っています。  プロパティとメソッドはプロトタイプに追加できますが、オブジェクトを別のプロトタイプに割り当てることはできません。  ただし、ユーザー定義オブジェクトは、新しいプロトタイプに割り当てることができます。  
  
 この言語リファレンスには、組み込みオブジェクトごとにメソッドとプロパティの一覧があり、オブジェクトのプロトタイプに含まれているメソッドとプロパティを調べることができます。  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]