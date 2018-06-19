---
title: toISOString メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
helpviewer_keywords:
- toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640272"
---
# <a name="toisostring-method-date-javascript"></a>toISOString メソッド (Date) (JavaScript)
日付を ISO 形式の文字列値として返します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>戻り値  
 国際標準化機構 (ISO) 形式の日付の文字列形式。  
  
## <a name="exceptions"></a>例外  
 場合`objDate`有効な日付が含まれていない、`RangeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 ISO 形式は、ISO 8601 形式の簡略化バージョンです。 詳細については、次を参照してください。[日付と時刻文字列](../../javascript/date-and-time-strings-javascript.md)です。  
  
 タイム ゾーンは UTC で出力にサフィックス Z で示されるでは常にします。  
  
## <a name="example"></a>例  
 `toISOString` メソッドの使用例を次に示します。  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [日付と時刻文字列](../../javascript/date-and-time-strings-javascript.md)