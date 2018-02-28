---
title: "match メソッド (String) (JavaScript) |Microsoft ドキュメント"
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
- match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>match メソッド (String) (JavaScript)
正規表現パターンを使って文字列に対して一致検索を実行し、検索結果を格納する配列を戻します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 検索対象とする `String` オブジェクトの名前またはリテラル文字列を指定します。  
  
 `rgExp`  
 必須です。 正規表現パターンおよび適用できるフラグを含む、正規表現オブジェクトを指定します。 このオブジェクトは、正規表現パターンとフラグを含む、変数名または文字列リテラルにもなります。  
  
## <a name="remarks"></a>コメント  
 パターンに一致する文字列が見つからなかった場合、`match` メソッドは `null` を返します。 一致する文字列が見つかった場合、`match` は配列を返し、さらにグローバルな `RegExp` オブジェクトのプロパティが検索結果を反映して更新されます。  
  
 場合、グローバル フラグ (`g`) が設定されていない要素の配列の 0 には、一致結果全体が、1 を使用して要素が含まれています。  *n*  、副次的に含まれています。 この動作の動作と同じ、 [exec メソッド (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)ときに、グローバル フラグが設定されていません。 かどうか、グローバル フラグが設定されて、要素 0 から *n* 発生したすべての一致項目が含まれています。  
  
 グローバル フラグが設定されていない場合、`match` のメソッドが返す配列には `input`、および `index` の 2 つのプロパティがあります。 `input` プロパティには、検索された文字列全体が格納されます。 `index` プロパティには、検索された文字列内の一致した部分文字列の位置が格納されます。  
  
 フラグ `i` が設定されている場合は、検索で大文字と小文字が区別されません。  
  
## <a name="example"></a>例  
 `match` メソッドの使用例を次に示します。  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [exec メソッド (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace メソッド (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [search メソッド (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test メソッド (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [正規表現プログラミング (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [代替と部分式 (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [前方参照 (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)