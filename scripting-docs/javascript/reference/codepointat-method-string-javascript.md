---
title: codePointAt メソッド (String) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633612"
---
# <a name="codepointat-method-string-javascript"></a>codePointAt メソッド (String) (JavaScript)
Unicode UTF-16 の文字のコード ポイントを返します。  
  
## <a name="syntax"></a>構文  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 String オブジェクト  
  
 `pos`  
 必須です。 文字の位置。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、すべての UTF-16 文字のコード ポイント値を返します。アストラル コード ポイント (16 進数字 4 桁を超えるコード ポイント) も含みます。  
  
 `pos` がゼロ (0) 未満か文字列のサイズを超える場合、戻り値は `undefined` です。  
  
## <a name="example"></a>例  
 `codePointAt` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
