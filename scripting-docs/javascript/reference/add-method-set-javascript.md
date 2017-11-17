---
title: "add メソッド (Set) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-set-javascript"></a>add メソッド (Set) (JavaScript)
セットに新しい要素を追加します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `setObj`  
 必須です。 `Set` オブジェクト。  
  
 `value`  
 必須です。 `Set` の新しい要素を指定します。  
  
## <a name="remarks"></a>コメント  
 新しい要素は、任意の型で、一意である必要があります。 `Set` に一意でない要素を追加する場合、新しい要素はコレクションに追加されません。  
  
## <a name="example"></a>例  
 次の例は、メンバーをセットに追加して取得する方法を示します。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]