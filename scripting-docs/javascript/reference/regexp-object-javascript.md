---
title: RegExp オブジェクト (JavaScript) |Microsoft ドキュメント
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
- RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640782"
---
# <a name="regexp-object-javascript"></a>RegExp オブジェクト (JavaScript)
正規表現パターンの結果に関する情報を格納する組み込みのグローバル オブジェクトに一致します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>コメント  
 必要な*プロパティ*引数のいずれかを指定できます、`RegExp`オブジェクト プロパティです。  
  
 `RegExp`オブジェクトを直接作成することはできませんが、使用可能では常にします。 成功した正規表現の検索が完了するまで、さまざまなプロパティの初期値、`RegExp`オブジェクトは、次のとおり。  
  
|プロパティ|短縮形|初期値|  
|--------------|---------------|-------------------|  
|インデックス||-1|  
|入力|$_|空の文字列。|  
|lastindex プロパティの値||-1|  
|lastMatch|$&|空の文字列。|  
|lastParen|$+|空の文字列。|  
|leftContext|$`|空の文字列。|  
|rightContext|$'|空の文字列。|  
|$1 - $9|$1 - $9|空の文字列。|  
  
 そのプロパティが成功した正規表現の検索が完了するまで、それらの値として定義されていません。  
  
 グローバル`RegExp`オブジェクトがないと混同しないでください、**正規表現**オブジェクト。 見えますが、同じように、それらは明確な違いです。 グローバル プロパティ`RegExp`オブジェクトには、これが発生すると、プロパティの中に一致した各文字列は継続的に更新された情報が含まれて、**正規表現**オブジェクトが発生した一致に関する情報のみを含みますインスタンスを**正規表現**です。  
  
## <a name="example"></a>例  
 次の例では、正規表現の検索を実行します。 一致項目が表示され、グローバルから submatches`RegExp`オブジェクト、およびによって返される配列から、`exec`メソッドです。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>プロパティ  
 [$1... 9 ドル プロパティ](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)&#124;です。[インデックス プロパティ](../../javascript/reference/index-property-regexp-javascript.md)&#124;です。[input プロパティ](../../javascript/reference/input-property-dollar-regexp-javascript.md)&#124;です。[lastIndex プロパティ](../../javascript/reference/lastindex-property-regexp-javascript.md)&#124;です。[lastMatch プロパティ](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)&#124;です。[lastParen プロパティ](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)&#124;です。[leftContext プロパティ](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)&#124;です。[rightContext プロパティ](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>メソッド  
 `RegExp`オブジェクトにメソッドがありません。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)