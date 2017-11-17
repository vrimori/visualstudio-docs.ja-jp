---
title: "prototype プロパティ (String) |Microsoft ドキュメント"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-string"></a>prototype プロパティ (文字列)
文字列のクラスのプロトタイプへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>コメント  
 `string`引数は文字列の名前。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。 オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、メソッドを追加するため、`String`オブジェクト、文字列の最後の要素の値を返す、関数宣言に追加して`String.prototype`、それを使用します。  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 すべての組み込み[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトが、`prototype`プロパティは読み取り専用です。 プロトタイプへのプロパティとメソッドを追加する可能性がありますが、オブジェクトが別のプロトタイプを割り当てられていない可能性があります。 ただし、ユーザー定義オブジェクトには、新しいプロトタイプを割り当てることがあります。  
  
 この言語リファレンスにおける組み込みオブジェクトごとに、メソッドおよびプロパティの一覧は、どのパーツが、オブジェクトのプロトタイプの一部とされていないを示します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]