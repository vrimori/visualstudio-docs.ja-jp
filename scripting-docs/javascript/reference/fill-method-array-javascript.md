---
title: "fill メソッド (Array) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4546bafb3fa3a8c242b8b7ef4ef2863ea86bf179
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="fill-method-array-javascript"></a>fill メソッド (Array) (JavaScript)
指定された値を配列に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 Array オブジェクト。  
  
 `value`  
 必須です。 配列の設定に使用する値です。  
  
 `start`  
 省略可能です。 配列値の設定に使用する開始インデックスです。 既定値は 0 です。  
  
 `end`  
 省略可能です。 配列値の設定に使用する終了インデックスです。 既定値は、`this` オブジェクトの length プロパティです。  
  
## <a name="remarks"></a>コメント  
 場合`start`が負の値、`start`として扱われます`length` +`start`ここで、`length`配列の長さです。 場合`end`が負の値、`end`として扱われる`length` +`end`です。  
  
## <a name="example"></a>例  
 次のコードの例は、値を配列に設定します。  
  
```JavaScript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]