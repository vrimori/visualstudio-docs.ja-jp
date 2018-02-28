---
title: "ignoreCase プロパティ (Regular Expression) (JavaScript) |Microsoft ドキュメント"
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
- ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ignorecase-property-regular-expression-javascript"></a>ignoreCase プロパティ (Regular Expression) (JavaScript)
IgnoreCase フラグの状態を示すブール値を返します (**すれば**) 正規表現で使用します。 既定値は**false**です。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>コメント  
 必要な`rgExp`参照がのインスタンス、`RegExp`オブジェクト。  
  
 **IgnoreCase**プロパティから返される**true**する ignoreCase フラグが、正規表現に設定されているしを返すかどうか**false**されていない場合。  
  
 IgnoreCase フラグを使用する場合は、検索を検索した文字列内のパターンを照合するときに大文字小文字の区別を無視するようにを示します。  
  
## <a name="example"></a>例  
 次の例では、使用、 **ignoreCase**プロパティです。 "ある gi"でを以下の関数に渡す場合、word のすべてのインスタンス「、」に置換されます、word 初期を含む"a"、"The"です。 これは、ignoreCase フラグを設定して、検索には、大文字小文字の区別が無視されるためです。 したがって"T"は"t"と同じ照合のためです。  
  
 この関数は許容される正規表現フラグの状態を示すブール値を返します**g**、**すれば**、および**m**です。 また、関数は、行われたすべての置換文字列を返します。  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>例  
 結果の出力を次に示します。  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [global プロパティ (Regular Expression)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline プロパティ (Regular Expression)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)