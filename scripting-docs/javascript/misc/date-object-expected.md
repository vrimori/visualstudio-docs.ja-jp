---
title: "日付オブジェクトが必要です |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-expected"></a>データ オブジェクトが必要です。
呼び出そうとした、 **Date.prototype.toString**または**Date.prototype.valueOf**メソッド以外の型のオブジェクトを`Date`です。 この呼び出し元のオブジェクト型でなければなりません`Date`です。 例:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを呼び出す、 **Date.prototype.toString**または**Date.prototype.valueOf**型のオブジェクトに対するメソッド`Date`です。  
  
## <a name="see-also"></a>関連項目  
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [getDate メソッド (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [組み込みオブジェクト](../../javascript/intrinsic-objects-javascript.md)