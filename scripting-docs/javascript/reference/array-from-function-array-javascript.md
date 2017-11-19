---
title: "Array.from 関数 (Array) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Array.from 関数 (Array) (JavaScript)
配列に似たオブジェクトまたは反復可能なオブジェクトから配列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `arrayLike`  
 必須です。 配列に似たオブジェクトまたは反復可能なオブジェクトです。  
  
 `mapfn`  
 省略可能です。 `arrayLike` で各要素に対して呼び出すマッピング関数です。  
  
 `thisArg`  
 省略可能です。 マッピング関数で `this` オブジェクトを指定します。  
  
## <a name="remarks"></a>コメント  
 `arrayLike` パラメーターは、`Set` オブジェクトなどの、インデックス付きの要素および `length` プロパティを持つオブジェクトか反復可能なオブジェクトでなければなりません。  
  
 省略可能なマッピング関数は、配列内の各要素に対して呼び出されます。  
  
## <a name="example"></a>例  
 次の例では、DOM 要素ノードのコレクションから配列を返します。  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>例  
 次の例では、文字の配列を返します。  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>例  
 次の例では、コレクションに含まれるオブジェクトの配列を返します。  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>例  
 次の例は、要素の値を変更するために、矢印構文とマッピング関数を使用する方法を示します。  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]