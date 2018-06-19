---
title: toString メソッド (String) 1 |Microsoft ドキュメント
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
ms.assetid: 56178c6e-cb08-4b34-824c-f63505379952
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b854dd6965515f6a64759dcae4a425a9a0bbb892
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640622"
---
# <a name="tostring-method-string-1"></a>toString メソッド (String) 1
文字列の文字列表現を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
string.toString()  
```  
  
## <a name="parameters"></a>パラメーター  
 `string`  
 必須です。 文字列として表現する配列。  
  
## <a name="return-value"></a>戻り値  
 文字列の文字列形式。  
  
## <a name="example"></a>例  
 次の例では、使用、 **toString**文字列を持つメソッドです。  
  
```JavaScript  
var string = "this is a test";  
var strStr = string.toString();  
document.write(strStr);  
  
// Output: this is a test  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]