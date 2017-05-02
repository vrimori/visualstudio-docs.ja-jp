---
title: "length プロパティ (Array) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array オブジェクト"
  - "Length プロパティ"
  - "length プロパティ (array)"
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# length プロパティ (Array) (JavaScript)
配列の長さを取得または設定します。  これは配列内で定義されている最後の要素のインデックスより 1 だけ大きい数値です。  
  
## 構文  
  
```  
  
numVar = arrayObj.length   
```  
  
## パラメーター  
 `numVar`  
 必須です。  任意の数値です。  
  
 `arrayObj`  
 必須です。  任意の `Array` オブジェクトを指定します。  
  
## 解説  
 JavaScript では配列は疎であり、配列内の要素が連続している必要はありません。  `length` プロパティは、必ずしも配列内の要素の数ではありません。  たとえば、次の配列定義で、`my_array.length` には 2 ではなく 7 が含まれています。  
  
```javascript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 `length` プロパティを以前の値より小さくする場合、配列は短縮されて、配列インデックスが `length` プロパティの新しい値と等しいかより大きいすべての要素が失われます。  
  
 Length プロパティを以前の値よりも大きくする場合、配列は拡張されて、新しく作成されるすべての要素に値 `undefined` が設定されます。  
  
 `length` プロパティの使用例を次に示します。  
  
```javascript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Internet Explorer 9 標準モード以降では、配列の初期化で組み込まれる末尾のコンマが、異なる方法で処理されます。