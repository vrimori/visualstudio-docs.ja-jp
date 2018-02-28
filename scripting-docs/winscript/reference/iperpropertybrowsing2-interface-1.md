---
title: "IPerPropertyBrowsing2 インターフェイス 1 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 インターフェイス 1
オブジェクトによって提供されているプロパティ ページの情報は、アクセスします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`GetDisplayString`|指定したプロパティを説明するテキスト文字列を返します。|  
|`MapPropertyToPage`|指定したプロパティを操作できる、プロパティ ページの CLSID を返します。|  
|`GetPredefinedStrings`|カウント対象の文字列の配列を返します (`LPOLESTR`ポインター)、指定されたプロパティで許容される許容値の説明を一覧表示します。|  
|`SetPredefinedValue`|プロパティの値をトークンで識別される定義済みの値に設定します`dwCookie.`|  
  
## <a name="requirements"></a>要件  
 ヘッダー: dbgprop.h