---
title: 列挙子オブジェクトが必要です |Microsoft ドキュメント
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
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632842"
---
# <a name="enumerator-object-expected"></a>列挙子オブジェクトが必要です。
呼び出そうとした、 **Enumerator.prototype.atEnd、Enumerator.prototype.item、Enumerator.prototype.moveFirst、** または**Enumerator.prototype.moveNext**他の型のオブジェクトのメソッド`Enumerator`です。 この呼び出し元のオブジェクト型でなければなりません`Enumerator`です。 この規則に違反するコードの例を次に示します。  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを呼び出す、 **Enumerator.prototype.atEnd**、 **Enumerator.prototype.item**、 **Enumerator.prototype.moveFirst**、または**Enumerator.prototype.moveNext**型のオブジェクトに対するメソッド`Enumerator`です。 かどうかをオブジェクトを見つけるには、`Enumerator`オブジェクトを使用します。  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Enumerator オブジェクト](../../javascript/reference/enumerator-object-javascript.md)