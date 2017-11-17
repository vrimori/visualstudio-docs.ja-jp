---
title: "論理 NOT 演算子 (!)(JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>論理 NOT 演算子 (!)(JavaScript)
2 つの式に対して論理否定を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *式*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 次に示す方法*結果*決定されます。  
  
|場合`expression`は|`result`は|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 すべての単項演算子など、 **!** 演算子は、次のように式を評価します。  
  
-   未定義に適用される場合または`null`式、実行時エラーが発生します。  
  
-   オブジェクトは、文字列に変換されます。  
  
-   文字列は、可能な場合は数値に変換されます。 それ以外の場合は、実行時エラーが発生しました。  
  
-   ブール値は、数字 (0 false の場合、true の場合は 1) として扱われます。  
  
 演算子は、結果の数に適用されます。  
  
 **!** 演算子場合、*式*がゼロ以外、*結果*は 0 です。 場合*式*ゼロ、*結果*は 1 です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビットごとの NOT 演算子 (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)