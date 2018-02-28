---
title: "ブール値を期待 |Microsoft ドキュメント"
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
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>ブール値が必要です。
呼び出そうとした、 **Boolean.prototype.toString**または**Boolean.prototype.valueOf**メソッド以外の型のオブジェクトを`Boolean`です。 この呼び出し元のオブジェクト型でなければなりません`Boolean`です。 例:  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ブール値を呼び出すだけ**. prototype.toString**または**Boolean.prototype.valueOf**型のオブジェクトに対するメソッド**ブール値。**  
  
## <a name="see-also"></a>関連項目  
 [Boolean オブジェクト](../../javascript/reference/boolean-object-javascript.md)   
 [データ型](../../javascript/data-types-javascript.md)   
 [プログラム フローの制御](../../javascript/controlling-program-flow-javascript.md)   
 [データのコピー、受け渡し、および比較](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)