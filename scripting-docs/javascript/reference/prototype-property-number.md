---
title: prototype プロパティ (数値) |Microsoft ドキュメント
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba8b8886b4fdbc48a662796863b1dfca019aec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639232"
---
# <a name="prototype-property-number"></a>prototype プロパティ (数値)
指定された数のクラスのプロトタイプへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
number.prototype  
```  
  
## <a name="remarks"></a>コメント  
 `number`引数は、数値の名前。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。 オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、メソッドを追加するため、`Number`オブジェクト (整数) の数の桁を返す、関数宣言に追加して`Number.prototype`、それを使用します。  
  
```JavaScript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 すべての組み込み[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトが、`prototype`プロパティは読み取り専用です。 プロトタイプへのプロパティとメソッドを追加する可能性がありますが、オブジェクトが別のプロトタイプを割り当てられていない可能性があります。 ただし、ユーザー定義オブジェクトには、新しいプロトタイプを割り当てることがあります。  
  
 この言語リファレンスにおける組み込みオブジェクトごとに、メソッドおよびプロパティの一覧は、どのパーツが、オブジェクトのプロトタイプの一部とされていないを示します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]