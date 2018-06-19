---
title: toLocaleString (Number) |Microsoft ドキュメント
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640832"
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
現在のロケールまたは指定されたロケールでの既定の書式を使用して、数値を文字列に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>パラメーター  
 `numberObj`  
 必須です。 変換対象の `Number` オブジェクト。  
  
 `locales`  
 省略可能です。 1 つ以上の言語またはロケールのタグを含むロケール文字列の配列。 複数のロケール文字列を含めると、最初のエントリが優先ロケールになるように、優先度の高いものから順に一覧表示されます。 このパラメーターを省略すると、JavaScript ランタイムの既定のロケールが使用されます。  
  
 `options`  
 省略可能です。 比較オプションを指定する 1 つ以上のプロパティを含むオブジェクト。  
  
## <a name="remarks"></a>コメント  
 Internet Explorer 11 以降では、`toLocaleString` は、`Intl.NumberFormat` パラメーターと `locales` パラメーターのサポートを追加する `options` を内部的に使用して、比較を実行します。 これらのパラメーターの詳細については、次を参照してください。 [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)です。  
  
> [!IMPORTANT]
>  `locales` パラメーターと `options` パラメーターは、一部のドキュメント モードとブラウザー バージョンではサポートされていません。 詳細については、「必要条件」を参照してください。  
  
> [!NOTE]
>  `locales` パラメーターを省略する場合、`toLocaleString` はユーザーに結果を表示する目的だけで使用してください。この関数の結果はコンピューターによって異なるため (このメソッドは現在のロケールを返します)、スクリプト内で値を計算する目的では使用しないでください。  
  
## <a name="example"></a>例  
 次の例は、パラメーターを指定せずに `toLocaleString` メソッドを使用する方法を示します。  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>例  
 次の例は、ロケールと比較オプションを指定して `toLocaleString` メソッドを使用する方法を示します。  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` パラメーターと `options` パラメーター:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [toLocaleDateString メソッド (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)