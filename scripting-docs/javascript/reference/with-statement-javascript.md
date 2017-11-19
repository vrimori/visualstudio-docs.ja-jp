---
title: "with ステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>with ステートメント (JavaScript)
ステートメントで使用する既定のオブジェクトを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>パラメーター  
 `object`  
 既定のオブジェクト。  
  
 `statements`  
 `object` を既定のオブジェクトとして使用する 1 つ以上のステートメントを指定します。  
  
## <a name="remarks"></a>コメント  
 一般に、`with` ステートメントは特定の場面で、記述するコードの量を少なくするために使用します。  
  
> [!WARNING]
>  厳密モードでは `with` は使用できません。 `with` を使用すると、コードの読み取りとデバッグが困難になる場合があるため、通常は避けるようにしてください。  
  
## <a name="example"></a>例  
 この例では、`Math` オブジェクトが繰り返し使用されています。  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>例  
 `with` ステートメントを使用してこの例を記述し直すと、コードがより簡潔になります。  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [this ステートメント](../../javascript/reference/this-statement-javascript.md)