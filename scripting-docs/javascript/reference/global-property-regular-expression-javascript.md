---
title: "global プロパティ (Regular Expression) (JavaScript) |Microsoft ドキュメント"
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
- Global
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- global property
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e2b0256fea60b7ab998c504e79565fc7028cd98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="global-property-regular-expression-javascript"></a>global プロパティ (Regular Expression) (JavaScript)
グローバル フラグの状態を示すブール値を返します (**g**) 正規表現で使用します。 既定値は**false**です。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```  
  
rgExp.global  
```  
  
## <a name="remarks"></a>コメント  
 必要な`rgExp`参照がのインスタンス、**正規表現**オブジェクト。  
  
 `global`プロパティから返される**true**かどうか、グローバル フラグは、正規表現に設定されを返します**false**されていない場合。  
  
 グローバル フラグを使用するは、最初の 1 つだけでなく、検索した文字列内のパターンのすべての項目を検索することを示します。 これは、グローバルに一致するとも呼ばれます。  
  
## <a name="example"></a>例  
 次の例では、使用、`global`プロパティです。 渡す場合**g**で、次に示す関数に、word のすべてのインスタンス「、」に置換されます、単語"a"です。 "The"、先頭の文字列の置換されませんので注意してください、**すれば**(大文字小文字を区別) フラグが関数に渡されません。  
  
 この関数には、許容される正規表現フラグに関連付けられているプロパティの条件が表示**g**、**すれば**、および**m**です。 関数では、文字列が行われたすべての置換も表示されます。  
  
```JavaScript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>例  
 結果の出力を次に示します。  
  
```JavaScript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [ignoreCase プロパティ (Regular Expression)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline プロパティ (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)