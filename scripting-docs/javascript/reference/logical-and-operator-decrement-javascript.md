---
title: 論理 AND 演算子 (&amp;&amp;) (JavaScript) |Microsoft ドキュメント
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
- '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638282"
---
# <a name="logical-and-operator-ampamp-javascript"></a>論理 AND 演算子 (&amp;&amp;) (JavaScript)
2 つの式について、論理積を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 任意の変数。  
  
 `expression1`  
 任意の式。  
  
 `expression2`  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 `expression1` が `false` に評価された場合、`result` は `expression1` です。 それ以外の場合、`result` は `expression2` です。 その結果、両方のオペランドが true である場合は、`true` が返され、それ以外の場合は、`false` が返されます。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は次の規則を使用して、非ブール値をブール値に変換します。  
  
-   すべてのオブジェクトは、`true` と見なされます。  
  
-   文字列は、空である場合、`false` と見なされます。  
  
-   `null` と `undefined` は `false` と見なされます。  
  
-   数値は、ゼロである場合、`false` となります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)