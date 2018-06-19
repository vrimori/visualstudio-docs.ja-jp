---
title: in 演算子 (JavaScript) |Microsoft ドキュメント
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637452"
---
# <a name="in-operator-javascript"></a>in 演算子 (JavaScript)
オブジェクト内にプロパティが存在するかどうかをテストします。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 必須です。 任意の変数。  
  
 `property`  
 必須です。 文字列式に評価される式。  
  
 `object`  
 必須です。 任意のオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `in`演算子は、オブジェクトがという名前のプロパティを持つかどうかを判定`property`です。 プロパティは、オブジェクトのプロトタイプ チェーンの一部であるかどうかも決定します。 オブジェクトのプロトタイプの詳細については、次を参照してください。[プロトタイプおよびプロトタイプの継承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)です。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`in`演算子。  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)