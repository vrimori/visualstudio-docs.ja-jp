---
title: toString メソッド (Number) |Microsoft ドキュメント
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6be170061faf4c2782c7247c80c55065c3a6742
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640392"
---
# <a name="tostring-method-number"></a>toString メソッド (数値)
数値の文字列表現を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
number.toString()  
```  
  
## <a name="parameters"></a>パラメーター  
 `number`  
 必須です。 文字列として表現する数です。  
  
## <a name="return-value"></a>戻り値  
 数値の文字列形式。  
  
## <a name="example"></a>例  
 次の例では、使用、 **toString**数値を持つメソッドです。  
  
```JavaScript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]