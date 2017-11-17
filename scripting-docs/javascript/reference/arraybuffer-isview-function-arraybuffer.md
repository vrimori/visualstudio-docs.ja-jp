---
title: "ArrayBuffer.isView 関数 (ArrayBuffer) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="arraybufferisview-function-arraybuffer"></a>ArrayBuffer.isView 関数 (ArrayBuffer)
オブジェクトがバッファーのビューを提供するかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 テストするオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `true` (後続のどちらかが真の場合):  
  
-   `object` は `DataView` オブジェクト。  
  
-   `object` は型指定された配列。  
  
 それ以外の場合、メソッドは `false` を返します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次の例では、`isView` 機能を使用した、型指定された配列と`DataView` オブジェクトのテストを説明します。  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Uint8ClampedArray オブジェクト](../../javascript/reference/uint8clampedarray-object-javascript.md)