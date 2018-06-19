---
title: prototype プロパティ (Boolean) |Microsoft ドキュメント
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52d2d241c4d550fe4491ea827fab9d586281242d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638842"
---
# <a name="prototype-property-boolean"></a>prototype プロパティ (Boolean)
Boolean のプロトタイプへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolean.prototype  
```  
  
## <a name="remarks"></a>コメント  
 `boolean` 引数は、オブジェクトの名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。 オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。 プロパティとメソッドをプロトタイプに追加することができますが、組み込みオブジェクトに別のプロトタイプを割り当てることはできません。  
  
 たとえば、`Boolean` オブジェクトに配列で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Boolean.prototype` に追加してから使用します。  
  
```JavaScript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]