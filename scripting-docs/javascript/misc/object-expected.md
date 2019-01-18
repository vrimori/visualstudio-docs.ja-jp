---
title: オブジェクトが必要です |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49d66c82081af06bf23a43922629a579a6d6f590
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345787"
---
# <a name="object-expected"></a>オブジェクトが必要です。
`Object` 以外の型のメソッドまたはプロパティを呼び出そうとしたか、または `Object` が必要なときに `Object` 以外の型の引数を渡しました。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `Object` 型のオブジェクトに対してのみメソッドまたはプロパティを呼び出します。  
  
-   オブジェクト以外の引数でエラーが発生した場合は、`Object` 型のオブジェクトを渡します。  
  
-   `Object` 型のオブジェクトの代わりに、未定義または null 参照のどちらが呼び出されているかを調べます。  
  
     たとえば、次のコードの myVar でこのエラーが生じた場合:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     代わりに次のコードを使用できます。  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Object オブジェクト](../../javascript/reference/object-object-javascript.md)   
 [オブジェクトと配列](../../javascript/objects-and-arrays-javascript.md)