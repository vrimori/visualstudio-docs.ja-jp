---
title: "予期される 16 進数字 |Microsoft ドキュメント"
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
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="expected-hexadecimal-digit"></a>16 進数の数字が必要です。
正しくない Unicode エスケープ シーケンスを作成したとします。 Unicode エスケープ シーケンスは、4 つの 16 進数字 (なくなるおよび未満) 後に、\u で始まります。 Unicode の 16 進数には、0 ~ 9 の数字のみ、A ~ F の英大文字、小文字アルファベットの a ~ f を含めることができます。 次の例では、正しい形式の Unicode エスケープ シーケンスを示します。  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   Unicode の 16 進数、\u で始まり、数字 0 ~ 9、大文字、A ~ F、小文字アルファベットの a ~ f; だけを格納してください。4 桁の数字をグループ化します。  
  
    > [!NOTE]
    >  リテラル テキスト \u を使用して、文字列に円記号を 2 を使用して、する場合 (\\\u)-最初の円記号をエスケープするために 1 つです。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../javascript/data-types-javascript.md)