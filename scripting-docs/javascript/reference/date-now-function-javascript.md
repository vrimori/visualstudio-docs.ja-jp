---
title: "Date.now 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="datenow-function-javascript"></a>Date.now 関数 (JavaScript)
現在の日付と時刻を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>戻り値  
 午前 0 時、1970 年 1 月 1 日と現在の日付と時刻までのミリ秒数。  
  
## <a name="remarks"></a>コメント  
 [GetTime メソッド](../../javascript/reference/gettime-method-date-javascript.md)までのミリ秒数を返します 1970 年 1 月 1 日と、指定された日付。  
  
 経過時間を計算し、日付を比較する方法については、次を参照してください。[を計算する日付と時刻 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)です。  
  
## <a name="example"></a>例  
 `now` メソッドの使用例を次に示します。  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>要件  
 Internet Explorer 9 よりも前にインストールされたバージョンでサポートされません。 ただしは次のドキュメント モードでサポートされて: Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準です。 サポートされても[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]アプリ。  
  
## <a name="see-also"></a>関連項目  
 [getTime メソッド (Date)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [日付と時刻の計算 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript メソッド](../../javascript/reference/javascript-methods.md)