---
title: "length プロパティ (String) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>length プロパティ (String) (JavaScript)
`String` オブジェクトの長さを返します。  
  
> [!WARNING]
>  JavaScript 文字列は不変であるため、文字列の長さを変更できません。  
  
## <a name="syntax"></a>構文  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>コメント  
 `length`プロパティには内の文字の数を示す整数が含まれています、`String`オブジェクト。 最後の文字、`String`オブジェクトのインデックスがありますは`length`- 1。  
  
## <a name="example"></a>例  
 `length` の使用例を次のコードに示します。 JavaScript 文字列は不変でありインプレースで変更することはできません。 ただし、配列に逆順にした文字列を作成しを呼び出す`join`に空の文字を区切り文字を含まない文字列が生成されます。  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]