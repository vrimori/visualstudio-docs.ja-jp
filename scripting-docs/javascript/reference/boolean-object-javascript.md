---
title: Boolean オブジェクト (JavaScript) |Microsoft ドキュメント
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
- boolean_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean object
- Boolean data type, Boolean object
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20695376e4935cf6ddc34f30e373df19575ece3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633912"
---
# <a name="boolean-object-javascript"></a>Boolean オブジェクト (JavaScript)
新しいブール値を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## <a name="parameters"></a>パラメーター  
 `boolObj`  
 必須です。 `Boolean` オブジェクトを代入する変数名を指定します。  
  
 `boolValue`  
 省略可能です。 新しいオブジェクトの初期のブール値。 場合`boolvalue`を省略すると、 `false`, 0, `null`、 `NaN`、ブール型のオブジェクトの初期値は、空の文字列または`false`です。 初期値は、それ以外の場合、`true`です。  
  
## <a name="remarks"></a>コメント  
 `Boolean`オブジェクトは、Boolean データ型のラッパー。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]暗黙的に使用、`Boolean`オブジェクトのブール型のデータ型に変換されるたびに、`Boolean`オブジェクト。  
  
 まれにインスタンス化、`Boolean`オブジェクトを明示的にします。  
  
## <a name="properties"></a>プロパティ  
 `Boolean` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[constructor プロパティ](../../javascript/reference/constructor-property-boolean.md)|ブール値を作成する関数を指定します。|  
|[prototype プロパティ](../../javascript/reference/prototype-property-boolean.md)|Boolean のプロトタイプへの参照を返します。|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>メソッド  
 `Boolean` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[toString メソッド](../../javascript/reference/tostring-method-boolean-1.md)|ブール値の文字列表現を返します。|  
|[valueOf メソッド](../../javascript/reference/valueof-method-boolean.md)|ブール値への参照を取得します。|  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]