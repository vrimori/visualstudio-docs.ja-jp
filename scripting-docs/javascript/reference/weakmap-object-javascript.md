---
title: "WeakMap オブジェクト (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WeakMap オブジェクト (JavaScript)
各キーがオブジェクトの参照である、キーと値のペアのコレクション。  
  
## 構文  
  
```  
weakmapObj = new WeakMap()  
```  
  
## 解説  
 `WeakMap` オブジェクトは列挙できません。  
  
 既存のキーを使用してコレクションに値を追加する場合、新しい値は元の値を置き換えます。  
  
 `WeakMap` オブジェクトでは、キー オブジェクトへの参照が「弱い」状態です。  これは、`WeakMap` がキー オブジェクトに発生するガベージ コレクションを阻止できないことを意味します。  キー オブジェクトへの参照 \(`WeakMap` 以外の参照\) がない場合、ガベージ コレクターはキー オブジェクトを収集することがあります。  
  
## プロパティ  
 `WeakMap` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[コンストラクター](../../javascript/reference/constructor-property-weakmap.md)|`WeakMap` を作成する関数を指定します。|  
|[prototype](../../javascript/reference/prototype-property-weakmap.md)|`WeakMap` のプロトタイプへの参照を返します。|  
  
## メソッド  
 `WeakMap` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|`WeakMap` からすべての要素を削除します。|  
|[delete](../../javascript/reference/delete-method-weakmap-javascript.md)|指定された要素を `WeakMap` から削除します。|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|指定された要素を `WeakMap` から戻します。|  
|[has](../../javascript/reference/has-method-weakmap-javascript.md)|`WeakMap` が指定した要素を格納している場合、`true` を返します。|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|`WeakMap` オブジェクトに新しい要素を追加します。|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|`WeakMap` の文字列表現を返します。|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## 使用例  
 次の例は、メンバーを `WeakMap` オブジェクトに追加して取得する方法を示します。  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]