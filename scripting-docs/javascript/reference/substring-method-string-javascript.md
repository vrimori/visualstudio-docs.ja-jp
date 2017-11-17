---
title: "substring メソッド (String) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="substring-method-string-javascript"></a>substring メソッド (String) (JavaScript)
内の指定位置にある部分文字列を返します、`String`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>パラメーター  
 `start`  
 必須です。 部分文字列の先頭を示す 0 から始まるインデックスの整数です。  
  
 `end`  
 省略可能です。 部分文字列の末尾を示す 0 から始まるインデックスの整数。 最大の部分文字列に文字が含まれていますを含めないことで示される文字`end`です。  
  
 場合`end`を省略すると、文字から成る`start`元の文字列の末尾までが返されます。  
  
## <a name="remarks"></a>コメント  
 `substring`メソッドから部分文字列を含む文字列を返します`start`までを含めず`end`です。  
  
 **Substring**メソッドの下限値を使用して`start`と`end`サブスト リングの開始点として。 たとえば、strvar.substring (0, 3**)** strvar.substring (3, 0) が、同じサブ文字列を返すとします。  
  
 いずれか`start`または`end`は`NaN`または負の値に置き換えられます 0 です。  
  
 部分文字列の長さが値の差の絶対値と等しい`start`と`end`です。 たとえば、strvar.substring (0, 3) で返される部分文字列の長さと strvar.substring (3, 0) は 3 です。  
  
## <a name="example"></a>例  
 次の例では、使用、 **substring**メソッドです。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [substr メソッド (String)](../../javascript/reference/substr-method-string-javascript.md)