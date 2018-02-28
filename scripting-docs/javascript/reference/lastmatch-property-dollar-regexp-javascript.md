---
title: "lastMatch プロパティ ($&amp;) (RegExp) (JavaScript) |Microsoft ドキュメント"
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
- $&
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastMatch property ($%)
- lastMatch property ($&)
ms.assetid: d223836d-5235-48a5-a926-d20764ad3f14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25991bf5b577d785fc4f7d8c6b2af14b93486000
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="lastmatch-property-amp-regexp-javascript"></a>lastMatch プロパティ ($&amp;) (RegExp) (JavaScript)
正規表現による検索で最後に一致した文字を返します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```  
  
RegExp.lastMatch  
```  
  
## <a name="remarks"></a>コメント  
 このプロパティに関連付けられているオブジェクトは、常にグローバル`RegExp`オブジェクト。  
  
 初期値、`lastMatch`プロパティは、空の文字列。 値、`lastMatch`プロパティが、一致するたびに変更します。  
  
## <a name="example"></a>例  
 `lastMatch` プロパティの使用例を次に示します。  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**: [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [$1... 9 ドル プロパティ (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index プロパティ (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input プロパティ ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex プロパティ (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastParen プロパティ ($ +) (RegExp)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [leftContext プロパティ ($') (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext プロパティ ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)