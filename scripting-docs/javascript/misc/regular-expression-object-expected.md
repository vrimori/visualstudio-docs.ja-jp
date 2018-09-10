---
title: 正規表現オブジェクトが必要です |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8e3c48b116680fe73d4cc318038cb2c13c4164
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280314"
---
# <a name="regular-expression-object-expected"></a>Regular Expression オブジェクトが必要です。
呼び出そうとしたか、 **RegExp.prototype.toString**または**RegExp.prototype.valueOf**メソッド以外の型のオブジェクトを`RegExp`します。 呼び出し元のオブジェクト型でなければなりません`RegExp`します。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを呼び出す、 **RegExp.prototype.toString**または**RegExp.prototype.valueOf**型のオブジェクトに対するメソッド`RegExp`します。  
  
## <a name="see-also"></a>関連項目  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現構文 (JavaScript)](https://msdn.microsoft.com/library/1400241x)