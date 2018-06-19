---
title: constructor プロパティ (Boolean) |Microsoft ドキュメント
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091da5342c4713c8eba646a8bd78c315a6a0fa48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636012"
---
# <a name="constructor-property-boolean"></a>constructor プロパティ (Boolean)
ブール値を作成する関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolean.constructor([[value])  
```  
  
#### <a name="parameters"></a>パラメーター  
 `boolean`  
 ブール型の名前。  
  
 `value`  
 省略可能です。 ブール型の値を指定します。 これは、数値の 1 または 0 の場合、文字列"true"または"false"です。  
  
## <a name="remarks"></a>コメント  
 `constructor`プロパティにブール型のオブジェクトのインスタンスを作成する関数への参照が含まれています。  
  
## <a name="example"></a>例  
 次の例は、コンス トラクター プロパティの使用方法を示しています。  
  
```JavaScript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]