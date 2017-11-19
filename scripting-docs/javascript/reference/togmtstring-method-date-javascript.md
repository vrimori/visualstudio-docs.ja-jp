---
title: "toGMTString メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="togmtstring-method-date-javascript"></a>toGMTString メソッド (Date) (JavaScript)
グリニッジ標準時を意味 Time(GMT) を使用して文字列に変換された日付を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>コメント  
 必要な`dateObj`参照は any`Date`オブジェクト。  
  
 `toGMTString`メソッドは、古い形式と下位互換性のためだけにに対して提供されます。 使用することをお勧め、`toUTCString`メソッド代わりにします。  
  
 `toGMTString`メソッドを返します、`String`日付を格納しているオブジェクトは、GMT 規則を使用して書式設定します。 戻り値の形式のとおりです:"00時 00分: 00 GMT の 05 Jan 1996"です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toUTCString メソッド (Date)](../../javascript/reference/toutcstring-method-date-javascript.md)