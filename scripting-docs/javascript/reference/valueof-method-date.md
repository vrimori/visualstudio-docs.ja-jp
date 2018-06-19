---
title: valueOf メソッド (Date) |Microsoft ドキュメント
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640462"
---
# <a name="valueof-method-date"></a>valueOf メソッド (日付)
午前 0 時、1970 年 1 月 1 日 (utc) からミリ秒単位で格納されている時刻の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>パラメーター  
 `date`オブジェクトは、日付の任意のインスタンス。  
  
## <a name="return-value"></a>戻り値  
 午前 0 時、1970 年 1 月 1 日 (utc) 以降のミリ秒数で格納されている時刻の値。 これは、値と同じ`getTime`です。  
  
## <a name="example"></a>例  
 次の例では、使用、`valueOf`日付を持つメソッドです。  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]