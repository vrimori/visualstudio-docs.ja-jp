---
title: Symbol.for 関数 (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b7e47c00fbaa321d71a3eeba79e523eee719fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639662"
---
# <a name="symbolfor-function-javascript"></a>Symbol.for 関数 (JavaScript)
指定したキーのシンボルを返します。キーが存在しない場合は、新しいキーで新しい symbol オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Symbol.for(key);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `key`  
 必須です。 シンボルのキー。説明としても使用されます。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、グローバル シンボル レジストリ内のシンボルを検索します。 シンボルを文字列としてシリアル化する場合は、グローバル シンボル レジストリを使用して、すべての参照で特定の文字列が適正なシンボルに対応するようにします。  
  
## <a name="example"></a>例  
  
```JavaScript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]