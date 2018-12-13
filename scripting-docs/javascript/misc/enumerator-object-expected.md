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
ms.openlocfilehash: 485e6e387f07fd3a54727f5f8e08c0a00743c6d9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935849"
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
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Enumerator オブジェクト](../../javascript/reference/enumerator-object-javascript.md)
