---
title: "WeakSet オブジェクト (JavaScript) | Microsoft Docs"
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# WeakSet オブジェクト (JavaScript)
任意の型の、一意のオブジェクトのコレクションです。  
  
## 構文  
  
```  
setObj = new WeakSet()  
```  
  
## 解説  
 `WeakSet` に一意でないオブジェクトを追加しようとすると、新しいオブジェクトはコレクションに追加されません。  
  
 `Set` とは異なり、オブジェクトだけがコレクションに追加されます。  任意の値をコレクションに追加することはできません。  
  
 `WeakSet` オブジェクトでは、セット内のオブジェクトへの参照が「弱い」状態です。  これは、`WeakSet` がオブジェクトで発生するガベージ コレクションを阻止しないことを意味します。  オブジェクトへの参照 \(`WeakSet` 以外の参照\) がない場合、ガベージ コレクターはオブジェクトを収集できます。  
  
 オブジェクトまたはオブジェクト メタデータのキャッシュが関係するシナリオでは、`WeakSet` \(または `WeakMap`\) が役立つ場合があります。  たとえば、拡張不能なオブジェクトのメタデータを `WeakSet` に格納したり、`WeakSet` を使用してユーザー イメージのキャッシュを作成したりできます。  
  
## プロパティ  
 `WeakSet` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|コンストラクター|セットを作成する関数を指定します。|  
|プロトタイプ|セットのプロトタイプへの参照を返します。|  
  
## メソッド  
 `WeakSet` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|追加|セットに要素を追加します。|  
|削除|指定された要素をセットから削除します。|  
|has|セットが指定した要素を格納している場合、`true` を返します。|  
  
## 使用例  
 次の例は、メンバーをセットに追加し、その後、メンバーが追加されたことを確認する方法を示しています。  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]