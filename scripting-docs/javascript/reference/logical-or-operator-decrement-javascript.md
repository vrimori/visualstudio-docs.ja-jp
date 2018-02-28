---
title: "論理 OR 演算子 (|)(JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '||'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '|| operator'
- logical OR operator
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80c8e1bcae57e13642a0c77ae75c7c2aac58ace6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="logical-or-operator--javascript"></a>論理 OR 演算子 (||) (JavaScript)
2 つの式に対して論理和を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression1 || expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *expression1*  
 任意の式。  
  
 *expression2*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 いずれかまたは両方の式に評価される場合**True**、*結果*は**True**です。 次の表に示す方法*結果*決定されます。  
  
|場合`expression1`は|および`expression2`は|`result`は|  
|-------------------------|--------------------------|---------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は次の規則を使用して、非ブール値をブール値に変換します。  
  
-   すべてのオブジェクトは、true と見なされます。  
  
-   文字列は空する場合にのみ、false と見なされます。  
  
-   `null`および未定義の場合は false と見なされます。  
  
-   番号は、false の場合、場合にのみ、0 です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)