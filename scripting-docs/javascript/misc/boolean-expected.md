---
title: ブール値が必要です |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868093"
---
# <a name="boolean-expected"></a>ブール値が必要です。
呼び出そうとしたか、 **Boolean.prototype.toString**または**Boolean.prototype.valueOf**メソッド以外の型のオブジェクトを`Boolean`します。 呼び出し元のオブジェクト型でなければなりません`Boolean`します。 例えば:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>このエラーを解決するには

- のみを呼び出す、 **Boolean.prototype.toString**または**Boolean.prototype.valueOf**型のオブジェクトに対するメソッド**ブール値。**

## <a name="see-also"></a>関連項目

- [Boolean オブジェクト](../../javascript/reference/boolean-object-javascript.md)
- [データの種類](../../javascript/data-types-javascript.md)
- [プログラム フローの制御](../../javascript/controlling-program-flow-javascript.md)
- [データのコピー、受け渡し、および比較](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)