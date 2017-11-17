---
title: "toUTCString メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toUTCString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC dates, converting to strings
- toUTCString method
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd5efc43152c1af2dd467b73dce235e8fe52f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="toutcstring-method-date-javascript"></a>toUTCString メソッド (Date) (JavaScript)
世界協定時刻 (UTC) を使用して文字列に変換された日付を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.toUTCString()   
```  
  
## <a name="remarks"></a>コメント  
 必要な`dateObj`参照は any`Date`オブジェクト。  
  
 `toUTCString`メソッドを返します、 `String` 、便利で UTC 規約を使用して書式設定する日付を格納しているオブジェクトがフォームを読みやすくします。  
  
## <a name="example"></a>例  
 `toUTCString` メソッドの使用例を次に示します。  
  
```JavaScript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toGMTString メソッド (Date)](../../javascript/reference/togmtstring-method-date-javascript.md)