---
title: "join メソッド (Array) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="join-method-array-javascript"></a>join メソッド (Array) (JavaScript)
指定した区切り記号で区切られた配列のすべての要素を追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 `Array` オブジェクト。  
  
 `separator`  
 省略可能です。 次の結果から、配列の 1 つの要素を区切るために使用文字列`String`です。 省略した場合、配列の要素は、コンマで区切られます。  
  
## <a name="remarks"></a>コメント  
 配列のいずれかの要素がある場合**未定義**または`null`、空の文字列として扱われます。  
  
## <a name="example"></a>例  
 次の例では、使用、**結合**メソッドです。  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)