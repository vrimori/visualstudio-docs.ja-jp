---
title: Enumerator オブジェクトが必要です |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 002c3a748af8f7fa5c21109adcb279f893b38965
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093003"
---
# <a name="enumerator-object-expected"></a>Enumerator オブジェクトが必要です
呼び出そうとしたか、 **Enumerator.prototype.atEnd、Enumerator.prototype.item、Enumerator.prototype.moveFirst、** または**Enumerator.prototype.moveNext**他の型のオブジェクトのメソッド`Enumerator`します。 呼び出し元のオブジェクト型でなければなりません`Enumerator`します。 この規則に違反するコードの例を次に示します。  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを呼び出す、 **Enumerator.prototype.atEnd**、 **Enumerator.prototype.item**、 **Enumerator.prototype.moveFirst**、または**Enumerator.prototype.moveNext**型のオブジェクトに対するメソッド`Enumerator`します。 オブジェクトかどうかを確認するを`Enumerator`オブジェクトを使用します。  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Enumerator オブジェクト](../../javascript/reference/enumerator-object-javascript.md)