---
title: "prototype プロパティ (エラー) | Microsoft Docs"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype プロパティ (エラー)
エラーのプロトタイプへの参照を返します。  
  
## 構文  
  
```  
  
error.prototype  
```  
  
## 解説  
 `error` 引数はエラーの名前です。  
  
 `prototype` プロパティを使用すると、Error が持つ機能の基本セットを知ることができます。  オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの動作を "継承" します。  
  
 たとえば、`Error` オブジェクトに配列内で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Error.prototype` に追加してから使用します。  
  
```javascript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 組み込み [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトはすべて、値の取得のみ可能な `prototype` プロパティを持っています。  プロパティとメソッドはプロトタイプに追加できますが、オブジェクトを別のプロトタイプに割り当てることはできません。  ただし、ユーザー定義オブジェクトは、新しいプロトタイプに割り当てることができます。  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]