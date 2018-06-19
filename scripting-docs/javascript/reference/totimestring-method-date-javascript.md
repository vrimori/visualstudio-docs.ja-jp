---
title: toTimeString メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640072"
---
# <a name="totimestring-method-date-javascript"></a>toTimeString メソッド (Date) (JavaScript)
時刻を文字列値として返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>コメント  
 必要な `objDate` 参照は `Date` オブジェクトです。  
  
 `toTimeString`メソッドは、現在のタイム ゾーンの時刻を表す文字列値を返します。  
  
## <a name="example"></a>例  
 次の例では、時刻 (UTC) 1970 年 1 月 1 日の深夜を過ぎた後 2000 ミリ秒に設定されているし、書き込まれます。  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [toDateString メソッド (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString メソッド (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)