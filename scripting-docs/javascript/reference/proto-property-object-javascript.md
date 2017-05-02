---
title: "__proto__ プロパティ (Object) (JavaScript) | Microsoft Docs"
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
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# __proto__ プロパティ (Object) (JavaScript)
指定されたオブジェクトの内部プロトタイプへの参照が含まれます。  
  
## 構文  
  
```  
object.__proto__  
```  
  
#### パラメーター  
 `object`  
 Required.  プロトタイプの設定対象となるオブジェクト。  
  
## 解説  
 `__proto__` プロパティを使用して、オブジェクトのプロトタイプを設定できます。  
  
 オブジェクトまたは関数は、新しいプロトタイプのすべてのメソッドとプロパティに加えて、新しいプロトタイプのプロトタイプ チェーン内のすべてのメソッドとプロパティを継承します。  オブジェクトが保持できるプロトタイプは 1 つだけであるため \(プロトタイプ チェーン内の継承されたプロトタイプは含まれない\)、`__proto__` プロパティを呼び出すと、前のプロトタイプが置き換えられます。  
  
 プロトタイプは拡張可能オブジェクトでのみ設定できます。  詳細については、「[Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)」を参照してください。  
  
> [!NOTE]
>  `__proto__` プロパティ名の先頭と末尾には 2 つのアンダースコアが付いています。  
  
## 使用例  
 オブジェクトのプロトタイプを設定する方法のコード例を次に示します。  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## 使用例  
 次のコード例は、プロパティをプロトタイプに追加することによってオブジェクトに追加する方法を示しています。  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## 使用例  
 次のコード例では、`String` オブジェクトで新しいプロトタイプを設定し、そのオブジェクトにプロパティを追加します。  
  
```javascript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [プロトタイプとプロトタイプ継承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)