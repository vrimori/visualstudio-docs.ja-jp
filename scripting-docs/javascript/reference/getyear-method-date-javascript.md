---
title: "getYear メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getyear-method-date-javascript"></a>getYear メソッド (Date) (JavaScript)
年を取得、`Date`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 年を返します。  
  
## <a name="remarks"></a>コメント  
  
> [!IMPORTANT]
>  このメソッドは、廃止されておりは旧バージョンとの互換性を保つのために提供します。 代わりに、`getFullYear` メソッドを使用してください。  
  
 [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]、し、Internet Explorer のバージョンで始まる[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]、返される値が格納されている年から 1900 を引いたです。 たとえば、1899 年は-1 として返され、100 として 2000 年が返されます。  
  
 [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)]を通じて[!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]数式は、年に依存します。 1900 ~ 1999 年、返される値はから 1900 を引いた格納されている年は、2 桁の値です。 範囲外の日付、4 桁の年が返されます。 たとえば、1996 は 96 として返されますは 1825 と 2025 が返されます。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getFullYear メソッド (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear メソッド (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear メソッド (Date)](../../javascript/reference/setyear-method-date-javascript.md)