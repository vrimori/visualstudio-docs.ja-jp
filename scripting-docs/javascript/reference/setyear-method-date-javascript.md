---
title: setYear メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640282"
---
# <a name="setyear-method-date-javascript"></a>setYear メソッド (Date) (JavaScript)
の年の値の設定、`Date`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numYear`  
 必須です。 1900 ~ 1999 年、これは数値から 1900 を引いた年と同じです。 日付の範囲内に、これは、4 桁の数値です。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、廃止されておりを保持する下位互換性を維持します。 代わりに、`setFullYear` メソッドを使用してください。  
  
 年を設定する、 `Date` 1997 年にオブジェクト呼び出し**setYear(97)** です。 2010 年を設定するには、呼び出す**setYear(2010)** です。 最後に、0 ~ 99 の範囲内で 1 年、年を設定する次のように使用します。、`setFullYear`メソッドです。  
  
> [!NOTE]
>  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Version 1.0、`setYear`によって提供される年の値を 1900 年の加算の結果となる値を使用して`numYear`年の値に関係なく、します。 たとえば、1899 年を設定する`numYear`-1 は、2000 年に設定して`numYear`100 です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getFullYear メソッド (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear メソッド (Date)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear メソッド (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)