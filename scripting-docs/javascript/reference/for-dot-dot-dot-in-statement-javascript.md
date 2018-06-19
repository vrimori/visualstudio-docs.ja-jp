---
title: データ型.. ステートメント (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636732"
---
# <a name="forin-statement-javascript"></a>for...in ステートメント (JavaScript)
オブジェクトの各プロパティまたは配列の各要素に対して 1 つまたは複数のステートメントを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>パラメーター  
 `variable`  
 必須です。 任意のプロパティ名の使用可能な変数`object`または任意の要素のインデックス、`array`です。  
  
 `object`, `array`  
 省略可能です。 オブジェクトまたは配列を反復処理します。  
  
 `statements`  
 省略可能です。 各プロパティに対して実行されるステートメントを 1 つまたは複数`object`またはの各要素`array`です。 複合ステートメントにすることもできます。  
  
## <a name="remarks"></a>コメント  
 値、ループの各イテレーションの開始時`variable`の次のプロパティ名は、`object`の次の要素のインデックスまたは`array`です。 使用してできます`variable`のプロパティを参照する、ループ内のステートメントのいずれかで`object`または要素の`array`します。  
  
 オブジェクトのプロパティは、確定的に割り当てられていません。 プロパティの名前のみで、インデックスを使用して特定のプロパティを指定できません。  
  
 配列を反復処理するは、0、1、2 は、要素の順序で実行されます。  
  
## <a name="example"></a>例  
 次の例では、使用、`for...in`ステートメントで、連想配列として使用します。  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>例  
 この例での使用、`for ... in`ステートメントを反復処理する場合、 `Array` expando プロパティを持つオブジェクト。  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  使用して、`Enumerator`コレクションのメンバーを反復処理するオブジェクト。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)