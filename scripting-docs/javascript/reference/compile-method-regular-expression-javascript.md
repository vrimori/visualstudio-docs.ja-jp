---
title: compile メソッド (Regular Expression) (JavaScript) |Microsoft ドキュメント
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
- compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634252"
---
# <a name="compile-method-regular-expression-javascript"></a>compile メソッド (Regular Expression) (JavaScript)
実行速度が速くの内部形式に正規表現をコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>パラメーター  
 `rgExp`  
 必須です。 インスタンス、**正規表現**オブジェクト。 変数の名前またはリテラルを指定できます。  
  
 *パターン*  
 必須です。 コンパイルされる正規表現パターンを含む文字列式  
  
 `flags`  
 省略可能です。 組み合わせることもできる、使用可能なフラグは次のとおりです。  
  
-   g (すべての出現箇所のグローバル検索*パターン*)  
  
-   i (大文字小文字を区別しない)  
  
-   m (複数行の検索)  
  
## <a name="remarks"></a>コメント  
 **コンパイル**メソッドに変換*パターン*を高速実行用の内部形式にします。 これにより、ループでの正規表現の効率的な使用例を示します。 正規表現をコンパイル処理が速く繰り返し、同じ式を再利用する場合。 利点は得られません、ただし、正規表現が変更された場合。  
  
## <a name="example"></a>例  
 次の例では、使用、**コンパイル**メソッド。  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)