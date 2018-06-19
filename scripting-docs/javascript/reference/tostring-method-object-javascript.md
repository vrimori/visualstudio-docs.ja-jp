---
title: toString メソッド (Object) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641662"
---
# <a name="tostring-method-object-javascript"></a>toString メソッド (Object) (JavaScript)
オブジェクトの値を表す文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>パラメーター  
 `objectname`  
 必須です。 文字列形式を求める対象のオブジェクト。  
  
 `radix`  
 省略可能です。 数値を文字列に変換するための基数を指定します。 この値は数値のみ使用されます。  
  
## <a name="remarks"></a>コメント  
 **ToString**メソッドは、組み込みのすべてのメンバー[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクト。 その動作は、オブジェクトの種類によって異なります。  
  
|オブジェクト|動作|  
|------------|--------------|  
|配列|要素、`Array`文字列に変換されます。 結果の文字列が表示され、コンマで区切っては連結されます。|  
|ブール型|場合は、ブール値は**true**、返します"`true`"です。 返しますそれ以外の場合、"`false`"です。|  
|日付|日付のテキスト表現を返します。|  
|エラー|関連するエラー メッセージを含む文字列を返します。|  
|関数|次の形式の文字列を返します場所*functionname*関数の名前を指定しますが**toString**メソッドが呼び出されました。<br /><br /> `function functionname( ) { [native code] }`|  
|数値|数値のテキスト表現を返します。|  
|String|値を返します、`String`オブジェクト。|  
|既定|返します`"[object objectname]"`ここで、`objectname`オブジェクトの種類の名前を指定します。|  
  
## <a name="example"></a>例  
 次の例では、使用、 **toString**基数の引数を持つメソッドです。 以下の関数の戻り値は、基数の変換テーブルです。  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **適用されます**:[オブジェクトの配列](../../javascript/reference/array-object-javascript.md)&#124;です。[Boolean オブジェクト](../../javascript/reference/boolean-object-javascript.md)&#124;です。[オブジェクトの日付](../../javascript/reference/date-object-javascript.md)&#124;です。[エラー オブジェクト](../../javascript/reference/error-object-javascript.md)&#124;です。[関数オブジェクト](../../javascript/reference/function-object-javascript.md)&#124;です。[オブジェクト番号](../../javascript/reference/number-object-javascript.md)&#124;です。[オブジェクトはオブジェクト](../../javascript/reference/object-object-javascript.md)&#124;です。[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)