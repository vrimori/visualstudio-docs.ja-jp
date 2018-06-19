---
title: test メソッド (Regular Expression) (JavaScript) |Microsoft ドキュメント
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
- test
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- test method
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e2d2c23821cba5149367c7b5a735fa471bf581
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640752"
---
# <a name="test-method-regular-expression-javascript"></a>test メソッド (Regular Expression) (JavaScript)
検索文字列のパターンが存在するかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
rgExp.test(str)   
```  
  
## <a name="parameters"></a>パラメーター  
 `rgExp`  
 必須です。 インスタンス、**正規表現**正規表現パターンおよび適用できるフラグを含むオブジェクト。  
  
 `str`  
 必須です。 検索を実行する対象の文字列です。  
  
## <a name="remarks"></a>コメント  
 **テスト**メソッドを確認かどうか、パターン、文字列内に存在し、返します、 **true**場合と**false**それ以外の場合。  
  
 グローバル プロパティ`RegExp`によってオブジェクトが変更されていない、**テスト**メソッドです。  
  
## <a name="example"></a>例  
 次の例では、使用、**テスト**メソッドです。 この例を使用するには、正規表現パターンと、文字列関数を渡します。 関数は文字列で正規表現パターンに出現する位置をテストし、その検索の結果を示す文字列を返します。  
  
```JavaScript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)