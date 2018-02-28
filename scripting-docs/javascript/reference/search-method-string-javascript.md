---
title: "search メソッド (String) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="search-method-string-javascript"></a>search メソッド (String) (JavaScript)
正規表現検索に一致する最初の部分文字列を検索します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 検索対象とする `String` オブジェクトの名前またはリテラル文字列を指定します。  
  
 `rgExp`  
 必須です。 インスタンス、**正規表現**正規表現パターンおよび適用できるフラグを含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 一致が見つかった場合、**検索**メソッドは最初の一致が発生した場所を文字列の先頭からのオフセットを示す整数値を返します。 一致するものが見つからない場合は、-1 を返します。  
  
## <a name="remarks"></a>コメント  
 設定することも、`i`のフラグを区別しないように検索をします。  
  
## <a name="example"></a>例  
 次の例では、使用、**検索**メソッドです。  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [exec メソッド (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match メソッド (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace メソッド (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [test メソッド (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [正規表現プログラミング (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)