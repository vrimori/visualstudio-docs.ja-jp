---
title: ビットごとの NOT 演算子 (~) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- "~"
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634262"
---
# <a name="bitwise-not-operator--javascript"></a>ビットごとの NOT 演算子 (~) (JavaScript)
式に対してビットごとの NOT (否定) を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *式*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 すべての単項演算子など、`~`演算子は次のように式を評価します。  
  
-   未定義に適用される場合または`null`式、実行時エラーが発生します。  
  
-   オブジェクトは、文字列に変換されます。  
  
-   文字列は、可能な場合は数値に変換されます。 それ以外の場合は、実行時エラーが発生しました。  
  
-   ブール値は、数字 (0 false の場合、true の場合は 1) として扱われます。  
  
 演算子は、結果の数に適用されます。  
  
 `~`演算子、式の値のバイナリ表現で、そのビットを反転させます。  
  
 式で 1 は、任意の数字では、結果に 0 になります。 式で 0 は、任意の数字では、結果の 1 になります。  
  
 次の例は、ビットごとの使用を示しています (~) 演算子ではありません。  
  
```  
var temp = ~5;  
```  
  
 結果として得られる値は、次の表に示すように、-6 です。  
  
|式|バイナリ値 (2 の補数)|10 進形式での値|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [論理 NOT 演算子 (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)