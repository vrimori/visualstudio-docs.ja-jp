---
title: constructor プロパティ (Set) |Microsoft ドキュメント
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea9af6d60c2ae8bc8a383c4cebbf0955e183895e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636212"
---
# <a name="constructor-property-set"></a>constructor プロパティ (Set)
セットを作成する関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
set.constructor  
```  
  
## <a name="remarks"></a>コメント  
 `set` はセットの名前で、必須です。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。 これには、`Global` オブジェクトと `Math` オブジェクトを除くすべての組み込み JavaScript オブジェクトが含まれています。 `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照があります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]