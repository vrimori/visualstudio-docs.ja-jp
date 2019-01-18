---
title: Date オブジェクトが必要です。 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349115"
---
# <a name="date-object-expected"></a>Date オブジェクトが必要です。
呼び出そうとしたか、 **Date.prototype.toString**または**Date.prototype.valueOf**メソッド以外の型のオブジェクトを`Date`します。 呼び出し元のオブジェクト型でなければなりません`Date`します。 例えば:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを呼び出す、 **Date.prototype.toString**または**Date.prototype.valueOf**型のオブジェクトに対するメソッド`Date`します。  
  
## <a name="see-also"></a>関連項目  
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [getDate メソッド (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [組み込みオブジェクト](../../javascript/intrinsic-objects-javascript.md)
