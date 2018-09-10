---
title: 無効な文字範囲の設定 (JavaScript) |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cc8feb9a33c2995e592f8031beb2e03605891d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282821"
---
# <a name="invalid-range-in-character-set-javascript"></a>文字セットの範囲が無効です (JavaScript)
範囲の設定に無効な文字を正規表現を作成しようとしました。 文字セットの 1 つの文字のみが a ~ z、0 ~ 9; など範囲する必要があります。文字セットでは、\w などの文字クラスを含めることはできません。 範囲の最初の文字が 2 つ目の範囲の文字の前にもあります。 例えば:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   正規表現の文字セットを作成して、正しい順序であることを確認するには、1 つだけの文字を使用します。  
  
## <a name="see-also"></a>関連項目  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現構文 (JavaScript)](https://msdn.microsoft.com/library/1400241x)