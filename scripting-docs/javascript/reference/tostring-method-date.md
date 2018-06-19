---
title: toString メソッド (Date) |Microsoft ドキュメント
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640252"
---
# <a name="tostring-method-date"></a>toString メソッド (日付)
日付の文字列表現を返します。 文字列の形式は、ロケールに依存します。 米国の英語 (en-us)、次のようには。  
  
 *曜日**月**日**時間*:*分*:*2 番目* *タイム ゾーン**年*  
  
## <a name="syntax"></a>構文  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>パラメーター  
 `date`  
 必須です。 文字列として表現する日付。  
  
## <a name="return-value"></a>戻り値  
 日付の文字列表現を返します。  
  
## <a name="example"></a>例  
 次の例では、使用、`toString`日付を持つメソッドです。  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]