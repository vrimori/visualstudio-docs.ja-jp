---
title: "prototype プロパティ (日付) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>prototype プロパティ (日付)
日付のプロトタイプへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>コメント  
 `date` 引数は、オブジェクトの名前です。  
  
 使用して、`prototype`プロパティを日付に機能の基本セットを提供します。 オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、`Date` オブジェクトに配列で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Date.prototype` に追加してから使用します。  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 すべての組み込み[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトが、`prototype`プロパティは読み取り専用です。 プロトタイプへのプロパティとメソッドを追加する可能性がありますが、オブジェクトが別のプロトタイプを割り当てられていない可能性があります。 ただし、ユーザー定義オブジェクトには、新しいプロトタイプを割り当てることがあります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]