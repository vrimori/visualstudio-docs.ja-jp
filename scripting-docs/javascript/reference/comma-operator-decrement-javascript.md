---
title: コンマ演算子 (,) (JavaScript) |Microsoft ドキュメント
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
- '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634182"
---
# <a name="comma-operator--javascript"></a>コンマ演算子 (,) (JavaScript)
2 つの式が順番に実行されるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 `expression1`  
 任意の式。  
  
 `expression2`  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 `,`演算子は、左から右へ順番に実行する式。 一般的な用途、`,`のインクリメント式では、演算子、`for`ループします。 例:  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for`ステートメントはループ内のすべての処理の最後に実行される 1 つの式のみを使用します。 `,`演算子は、両方の変数をインクリメントするために 1 つの式として扱われる複数の式を使用します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)