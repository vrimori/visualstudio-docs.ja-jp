---
title: "ArrayBuffer.isView 関数 (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ArrayBuffer.isView 関数 (ArrayBuffer)
オブジェクトがバッファーのビューを提供するかどうかを決定します。  
  
## 構文  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### パラメーター  
 `object`  
 必ず指定します。  テストするオブジェクト。  
  
## 戻り値  
 `true` \(後続のどちらかが真の場合\):  
  
-   `object` は `DataView` オブジェクト。  
  
-   `object` は型指定された配列。  
  
 それ以外の場合、メソッドは `false` を返します。  
  
## 解説  
  
## 使用例  
 次の例では、`isView` 機能を使用した、型指定された配列と`DataView` オブジェクトのテストを説明します。  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 参照  
 [Uint8ClampedArray オブジェクト](../../javascript/reference/uint8clampedarray-object-javascript.md)