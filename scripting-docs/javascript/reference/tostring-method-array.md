---
title: toString メソッド (Array) |Microsoft ドキュメント
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640412"
---
# <a name="tostring-method-array"></a>toString メソッド (配列)
配列の文字列表現を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>パラメーター  
 `array`  
 必須です。 文字列として表現する配列。  
  
## <a name="return-value"></a>戻り値  
 配列の文字列形式。  
  
## <a name="remarks"></a>コメント  
 要素、`Array`文字列に変換されます。 結果の文字列がコンマで区切ってし、連結されています。  
  
## <a name="example"></a>例  
 次の例では、使用、 **toString**配列を持つメソッドです。  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]