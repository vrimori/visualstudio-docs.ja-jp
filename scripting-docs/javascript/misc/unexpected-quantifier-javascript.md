---
title: "予期しない量指定子 (JavaScript) |Microsoft ドキュメント"
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="unexpected-quantifier-javascript"></a>予期しない量指定子です (JavaScript)
正規表現検索パターンを作成するときに、無効な繰り返し係数を持つパターン要素を作成しました。 たとえば、パターン  
  
```  
/^+/  
```  
  
 無効ため要素 ^ (入力の先頭) が繰り返し係数を持つことはできません。 次の表には、繰り返し要素を持つことができない要素が一覧表示します。  
  
|要素|説明|  
|-------------|-----------------|  
|^|入力の先頭|  
|$|入力の終わり|  
|\b|ワード境界|  
|\B|ワード境界以外|  
|*|0 個以上の繰り返し|  
|+|1 つ以上の繰り返し|  
|?|0 個または 1 回の繰り返し|  
|{n}|n 回の繰り返し|  
|{n}|n またはそれ以上の繰り返し|  
|{n, m}|N m 繰り返しからから|  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   検索パターンの要素には、法的な繰り返し要素のみが含まれています。 を確認します。  
  
## <a name="see-also"></a>関連項目  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)