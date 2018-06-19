---
title: constructor プロパティ (String) |Microsoft ドキュメント
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636062"
---
# <a name="constructor-property-string"></a>constructor プロパティ (文字列)
文字列を作成する関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>コメント  
 必要な`string`文字列の名前を指定します。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。 すべての組み込みが含まれます[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトを除く、`Global`と`Math`オブジェクト。 `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照があります。  
  
## <a name="example"></a>例  
 次の例は、コンス トラクター プロパティの使用方法を示しています。  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]