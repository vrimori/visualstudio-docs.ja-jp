---
title: constructor プロパティ (WeakMap) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c7340e1e5eeff9a80e231cf1aa49443adc94e72
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636042"
---
# <a name="constructor-property-weakmap"></a>constructor プロパティ (WeakMap)
`WeakMap` オブジェクトを作成する関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
weakmap.constructor  
```  
  
## <a name="remarks"></a>コメント  
 `weakmap` 引数は必須で、`WeakMap` オブジェクトの名前を指定します。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。 これには、`Global` オブジェクトと `Math` オブジェクトを除くすべての組み込み JavaScript オブジェクトが含まれています。 `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照があります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]