---
title: "toLocaleString メソッド (Object) (JavaScript) |Microsoft ドキュメント"
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
- toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>toLocaleString メソッド (Object) (JavaScript)
特定の日付を返しますが、現在のロケールを使用して文字列に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>コメント  
 必要な`dateObj`は any`Date`オブジェクト。  
  
 `toLocaleString`メソッドを返します、`String`を現在のロケールの長い既定形式で書き込まれた日付を含むオブジェクト。  
  
-   1999 西暦 1601 から日の日付は、ユーザーのコントロール パネルの地域設定に従って書式設定されました。  
  
-   既定の形式をこの範囲外の日付の**toString**メソッドを使用します。  
  
 たとえば、米国の州、`toLocaleString`を返します"01/05/96 00時 00分: 00"の 1 月 5 日です。 返します、ヨーロッパで"96 01/05/00時 00分: 00"の同じの日付では、ヨーロッパの規則としては、日の前の月に、です。  
  
> [!NOTE]
>  `toLocaleString`結果を表示するユーザーに対してのみ使用する必要があります。ことはありません使用してください、基準として計算スクリプト内での返された結果はコンピューター固有。  
  
## <a name="example"></a>例  
 `toLocaleString` メソッドの使用例を次に示します。  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[オブジェクトの配列](../../javascript/reference/array-object-javascript.md)&#124;です。[オブジェクトの日付](../../javascript/reference/date-object-javascript.md)&#124;です。[オブジェクト番号](../../javascript/reference/number-object-javascript.md)&#124;です。[オブジェクトはオブジェクト](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toLocaleDateString メソッド (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)