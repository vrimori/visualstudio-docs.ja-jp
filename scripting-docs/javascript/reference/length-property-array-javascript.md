---
title: length プロパティ (Array) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637922"
---
# <a name="length-property-array-javascript"></a>length プロパティ (Array) (JavaScript)
配列の長さを取得または設定します。 これは配列内で定義されている最後の要素のインデックスより 1 だけ大きい数値です。  
  
## <a name="syntax"></a>構文  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>パラメーター  
 `numVar`  
 必須です。 任意の数値です。  
  
 `arrayObj`  
 必須です。 任意の `Array` オブジェクトを指定します。  
  
## <a name="remarks"></a>コメント  
 JavaScript では配列は疎であり、配列内の要素が連続している必要はありません。 `length` プロパティは、必ずしも配列内の要素の数ではありません。 たとえば、次の配列定義で、`my_array.length` には 2 ではなく 7 が含まれています。  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 `length` プロパティを以前の値より小さくする場合、配列は短縮されて、配列インデックスが `length` プロパティの新しい値と等しいかより大きいすべての要素が失われます。  
  
 Length プロパティを以前の値よりも大きくする場合、配列は拡張されて、新しく作成されるすべての要素に値 `undefined` が設定されます。  
  
 `length` プロパティの使用例を次に示します。  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Internet Explorer 9 標準モード以降では、配列の初期化で組み込まれる末尾のコンマが、異なる方法で処理されます。