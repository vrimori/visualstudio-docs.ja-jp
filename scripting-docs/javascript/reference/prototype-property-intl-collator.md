---
title: prototype プロパティ (Intl.Collator) |Microsoft ドキュメント
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639122"
---
# <a name="prototype-property-intlcollator"></a>prototype プロパティ (Intl.Collator)
Collator のプロトタイプへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>コメント  
 `collator` 引数は、Collator の名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。 オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、`Intl.Collator` オブジェクトにセット内で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Intl.Collator.prototype` に追加してから使用します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]