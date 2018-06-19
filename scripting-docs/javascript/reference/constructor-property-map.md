---
title: constructor プロパティ (Map) |Microsoft ドキュメント
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
ms.assetid: a90d6a29-bd64-4e01-8d2f-988b7e3e4a24
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7050f4a7eab149862c08ea755361b5bd0d297299
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636032"
---
# <a name="constructor-property-map"></a>constructor プロパティ (Map)
マップを作成する関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
map.constructor  
```  
  
## <a name="remarks"></a>コメント  
 `map` はマップの名前で、必須です。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。 これには、`Global` オブジェクトと `Math` オブジェクトを除くすべての組み込み JavaScript オブジェクトが含まれています。 `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照があります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]