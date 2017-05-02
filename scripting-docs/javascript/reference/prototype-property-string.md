---
title: "prototype プロパティ (文字列) | Microsoft Docs"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype プロパティ (文字列)
指定された文字列のクラスのプロトタイプへの参照を返します。  
  
## 構文  
  
```  
  
string.prototype  
```  
  
## 解説  
 `string` 引数は、文字列の名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの動作を "継承" します。  
  
 たとえば、`String` オブジェクトに文字列内の要素の値を返すメソッドを追加する場合は、関数を宣言して `String.prototype` に追加してから使用します。  
  
```javascript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 組み込み [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトはすべて、値の取得のみ可能な `prototype` プロパティを持っています。  プロパティとメソッドはプロトタイプに追加できますが、オブジェクトを別のプロトタイプに割り当てることはできません。  ただし、ユーザー定義オブジェクトは、新しいプロトタイプに割り当てることができます。  
  
 この言語リファレンスには、組み込みオブジェクトごとにメソッドとプロパティの一覧があり、オブジェクトのプロトタイプに含まれているメソッドとプロパティを調べることができます。  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]