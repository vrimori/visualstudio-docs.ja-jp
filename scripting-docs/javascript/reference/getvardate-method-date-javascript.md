---
title: "getVarDate メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>getVarDate メソッド (Date) (JavaScript)
`Date` オブジェクトからの VT_DATE 値を返します。  
  
> [!WARNING]
>  このメソッドは、Internet Explorer でのみサポートされます。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 VT_DATE 値を返します。  
  
## <a name="remarks"></a>コメント  
 `getVarDate` メソッドは、JavaScript コードが、COM オブジェクト、ActiveX オブジェクト、または VT_DATE 形式の日付値を受け入れて返すその他のオブジェクトと対話する場合に使用されます。 これらには、Visual Basic および Visual Basic Scripting Edition (VBScript) のオブジェクトが含まれます。 戻り値の実際の形式は、地域の設定によって異なります。  
  
## <a name="requirements"></a>要件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「 [バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getDate メソッド (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse 関数](../../javascript/reference/date-parse-function-javascript.md)