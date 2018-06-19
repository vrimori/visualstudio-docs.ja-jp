---
title: getTimezoneOffset メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637052"
---
# <a name="gettimezoneoffset-method-date-javascript"></a>getTimezoneOffset メソッド (Date) (JavaScript)
ローカル コンピューターの時刻と世界協定時刻 (UTC) の差を分単位を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 現在のコンピューター上の時間間隔を分単位の数を返します (クライアント コンピューターまたはサーバー コンピューター、サーバー スクリプトからこのメソッドが呼び出された場合) と UTC です。 現在のコンピューターのローカル時刻は UTC (たとえば、日本語) 場合に、現在のコンピューターのローカル時刻が UTC (Pacific Daylight Time など) と負の値の背後には場合は正の値です。 年 12 月 1 日ニューヨークのサーバーは、ロサンゼルスにあるクライアントから接続される場合`getTimezoneOffset`サーバーで実行される場合、クライアント、または 300 で実行される場合は、480 を返します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 `getTimezoneOffset` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getTime メソッド (Date)](../../javascript/reference/gettime-method-date-javascript.md)