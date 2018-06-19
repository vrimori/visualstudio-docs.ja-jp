---
title: Regular Expression オブジェクト (JavaScript) |Microsoft ドキュメント
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
- RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642042"
---
# <a name="regular-expression-object-javascript"></a>Regular Expression オブジェクト (JavaScript)
正規表現パターンとそのパターンを適用する方法を示すフラグとを含むオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>構文  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>パラメーター  
 *re*  
 必須です。 正規表現パターンが割り当てられている変数の名前。  
  
 *パターン*  
 必須です。 使用する正規表現パターン。 構文 1 を使用する場合、「/」文字でパターンを区切ります。 構文 2 を使用する場合、パターンを引用符で囲みます。  
  
 `flags`  
 省略可能です。 構文 2 を使用する場合、フラグを引用符で囲みます。 組み合わせることもできる、使用可能なフラグは次のとおりです。  
  
-   g (すべての出現箇所のグローバル検索*パターン*)  
  
-   i (大文字小文字を区別しない)  
  
-   m (複数行の検索)  
  
-   u (unicode)、EcmaScript 6 のにより[Unicode 機能](../../javascript/advanced/special-characters-javascript.md)します。 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] でのみサポートされています。  
  
-   y (付箋一致)、正規表現の `lastIndex` プロパティで一致を検索します (それ以降のインデックスでは検索しません)。 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] でサポートされています。  
  
## <a name="remarks"></a>コメント  
 **正規表現**オブジェクト混同しないように、グローバルな`RegExp`オブジェクト。 同じように見えますが、それらは別個のオブジェクトです。 プロパティ、**正規表現**オブジェクトが 1 つの特定に関する情報だけを含む**正規表現**のグローバル プロパティの中に、インスタンス`RegExp`オブジェクトを含める継続的に発生している各一致に関する情報を更新します。  
  
 **正規表現**オブジェクトは、文字の組み合わせの文字列を検索するときに使用されるパターンを格納します。 後に、**正規表現**オブジェクトが作成された、文字列メソッドに渡されますか、または文字列が正規表現メソッドのいずれかに渡されます。 実行された最新の検索についての情報は、グローバル `RegExp` オブジェクトに格納されます。  
  
 検索文字列があらかじめ分かっている場合には、構文 1 を使用します。 ユーザー入力から取得される文字列の場合など、検索文字列が頻繁に変更される場合や不明の場合には、構文 2 を使用します。  
  
 *パターン*引数が使用する前に、内部形式にコンパイルされています。 構文 1 では、*パターン*スクリプトが読み込まれる際にコンパイルします。 構文 2 では、*パターン*使用の直前にコンパイルされた場合や、**コンパイル**メソッドが呼び出されます。  
  
## <a name="example"></a>例  
 次の例では、使用、**正規表現**オブジェクト (re) とその関連フラグと正規表現パターンが含まれたオブジェクトを作成します。 この場合は、その結果、**正規表現**でオブジェクトを使用して、`match`メソッド。  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>例  
 次の例では、複数のインスタンスを検索するように正規表現パターンを更新します。  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>例  
 /y フラグを使用するとき、一致が見つかった場合は、`lastindex` が最後の一致の後にある次の文字のインデックスに更新されます。 一致が見つからない場合は、`lastindex` が 0 にリセットされます。  
  
 次の例では、/y フラグと `lastIndex` プロパティを使用して、特定のインデックス位置で一致するものを検索します。  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>プロパティ  
 [グローバル プロパティ](../../javascript/reference/global-property-regular-expression-javascript.md)&#124;です。[ignoreCase プロパティ](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)&#124;です。[multiline プロパティ](../../javascript/reference/multiline-property-regular-expression-javascript.md)&#124;です。[source プロパティ](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>メソッド  
 [compile メソッド](../../javascript/reference/compile-method-regular-expression-javascript.md)&#124;です。[exec メソッド](../../javascript/reference/exec-method-regular-expression-javascript.md)&#124;です。[テスト メソッド](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 u フラグは [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] でサポートされています。  
  
 y フラグは [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] でサポートされています。  
  
## <a name="see-also"></a>関連項目  
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)