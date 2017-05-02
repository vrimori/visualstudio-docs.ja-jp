---
title: "Symbol.for 関数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Symbol.for 関数 (JavaScript)
指定したキーのシンボルを返します。キーが存在しない場合は、新しいキーで新しい symbol オブジェクトを作成します。  
  
## 構文  
  
```vb  
Symbol.for(key);  
```  
  
#### パラメーター  
 `key`  
 必須。  シンボルのキー。説明としても使用されます。  
  
## 解説  
 このメソッドは、グローバル シンボル レジストリ内のシンボルを検索します。  シンボルを文字列としてシリアル化する場合は、グローバル シンボル レジストリを使用して、すべての参照で特定の文字列が適正なシンボルに対応するようにします。  
  
## 使用例  
  
```javascript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]