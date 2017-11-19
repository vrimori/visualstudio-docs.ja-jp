---
title: "Math.sign 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="mathsign-function-javascript"></a>Math.sign 関数 (JavaScript)
数値が正、負、または 0 のいずれであるかを示す、数値の符号を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>コメント  
 必須の `number` 引数は、符号を必要とする数値式です。  
  
 戻り値は次のいずれかになります。  
  
-   `number` が `NaN` の場合は `NaN`。  
  
-   -0 場合`number`は 0 です。  
  
-   `number` が +0 の場合は +0。  
  
-   -1 場合`number`が負の値および not - 0 です。  
  
-   `number` が正の値で、+0 ではない場合は +1。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]