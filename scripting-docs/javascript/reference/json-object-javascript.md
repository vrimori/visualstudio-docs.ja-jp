---
title: JSON オブジェクト (JavaScript) |Microsoft ドキュメント
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
- JSON
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JSON object
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5310132368f665c6734c469a67636d33a08858d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638052"
---
# <a name="json-object-javascript"></a>JSON オブジェクト (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の値と JSON (JavaScript Object Notation) 形式間で変換を行う関数を提供する組み込みオブジェクト。 `JSON.stringify` 関数は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値を JSON テキストにシリアル化します。 `JSON.parse` 関数は、JSON テキストを逆シリアル化して [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
JSON.[method]  
  
```  
  
## <a name="parameters"></a>パラメーター  
 `Method`  
 必ず指定します。 `JSON` オブジェクトのメソッドの 1 つの名前です。  
  
## <a name="remarks"></a>コメント  
 `JSON` 演算子を使用して `new` オブジェクトを作成することはできません。 この操作を行うと、エラーが発生します。 ただし、`JSON` オブジェクトをオーバーライドするか、変更することはできます。  
  
 スクリプト エンジンは、エンジンが読み込まれるときに `JSON` オブジェクトを作成します。 このメソッドは、スクリプト内でいつでも使用できます。  
  
 組み込みの `JSON` オブジェクトを使用するには、スクリプトで定義されている別の `JSON` オブジェクトでそれをオーバーライドしていないことを確認します。 `JSON` オブジェクトの存在を検出する既存のスクリプト ステートメントでは評価が異なるため、これらのステートメントの変更が必要になる場合があります。 このコード例を次に示します。  
  
```JavaScript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 前の例では、`!this.JSON` が、[!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)] では false と評価します。 したがって、`if` ステートメント内のコードは実行されません。  
  
## <a name="functions"></a>関数  
 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)  
  
 [JSON.stringify 関数](../../javascript/reference/json-stringify-function-javascript.md)  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [toJSON メソッド (Date)](../../javascript/reference/tojson-method-date-javascript.md)   
 [JavaScript オブジェクト](../../javascript/reference/javascript-objects.md)   
 [ハブ テンプレートのサンプル アプリ (Windows ストア)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)