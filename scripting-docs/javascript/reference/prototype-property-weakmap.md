---
title: prototype プロパティ (WeakMap) |Microsoft ドキュメント
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639252"
---
# <a name="prototype-property-weakmap"></a>prototype プロパティ (WeakMap)
`WeakMap` オブジェクトのプロトタイプへの参照を戻します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>コメント  
 `weakmap` 引数は、`WeakMap` オブジェクトの名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。 オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、`WeakMap` オブジェクトに `WeakMap` 内で最も大きな要素の値を戻すメソッドを追加する場合は、関数を宣言して `WeakMap.prototype` に追加してから使用します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]