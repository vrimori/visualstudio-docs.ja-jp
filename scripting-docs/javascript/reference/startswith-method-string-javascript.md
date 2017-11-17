---
title: "startsWith メソッド (String) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 871def4a-0f96-4675-b6ff-2349f4996511
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74970a9a3bfe280e91f2df39340732eda8664142
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="startswith-method-string-javascript"></a>startsWith メソッド (String) (JavaScript)
文字列または部分文字列が別の指定された文字列で開始するかどうかを示す値を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
  
stringObj.startsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 検索対象の文字列オブジェクト。  
  
 `str`  
 必須です。 検索文字列。  
  
 `position`  
 省略可能です。 文字列オブジェクトで検索する最初の文字の位置 (0 で始まります)。  
  
## <a name="return-value"></a>戻り値  
 `position` で始まる文字列が検索文字列で開始する場合、`startsWith` メソッドは `true` を返します。それ以外の場合は、`false` を返します。  
  
## <a name="exceptions"></a>例外  
 `str` が `RegExp` の場合、`TypeError` がスローされます。  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]