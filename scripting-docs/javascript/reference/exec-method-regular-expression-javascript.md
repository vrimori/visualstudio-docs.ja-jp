---
title: exec メソッド (Regular Expression) (JavaScript) |Microsoft ドキュメント
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
- exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637042"
---
# <a name="exec-method-regular-expression-javascript"></a>exec メソッド (Regular Expression) (JavaScript)
正規表現パターンを使用して文字列の検索を実行し、その検索の結果を含む配列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>パラメーター  
 `rgExp`  
 必須です。 インスタンス、**正規表現**正規表現パターンおよび適用できるフラグを含むオブジェクト。  
  
 `str`  
 必須です。 検索対象とする `String` オブジェクトの名前またはリテラル文字列を指定します。  
  
## <a name="remarks"></a>コメント  
 パターンに一致する文字列が見つからなかった場合、`exec` メソッドは `null` を返します。 一致する文字列が見つかった場合、`exec` は配列を返し、さらにグローバルな `RegExp` オブジェクトのプロパティが検索結果を反映して更新されます。 配列の要素 0 には、一致した文字列全体、要素が 1 - が含まれています。  *n* 一致内で発生した任意の副次的に含まれています。 動作に同じ動作であり、`match`グローバル フラグを設定しないメソッド (**g**) を設定します。  
  
 正規表現では、グローバル フラグが設定されている場合`exec`の値によって示される位置から始まる文字列を検索`lastIndex`です。 グローバル フラグが設定されていない場合`exec`の値を無視`lastIndex`検索文字列の先頭から開始します。  
  
 によって返される配列、`exec`メソッドが 3 つのプロパティを持つ**入力**、**インデックス**と**lastIndex です。** **入力**プロパティには、検索した文字列全体が含まれています。 **インデックス**プロパティには、検索された文字列内で一致した部分文字列の位置が含まれています。 `lastIndex`プロパティには、一致している最後の文字の直後の位置が含まれています。  
  
## <a name="example"></a>例  
 次の例では、使用、`exec`メソッド。  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [match メソッド (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search メソッド (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test メソッド (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [正規表現プログラミング (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)