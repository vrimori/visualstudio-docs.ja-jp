---
title: "IPerPropertyBrowsing2 インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2 インターフェイス"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IPerPropertyBrowsing2 インターフェイス
オブジェクトが提供するプロパティ ページ内の情報にアクセスします。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|`GetDisplayString`|指定したプロパティを説明する文字列を返します。|  
|`MapPropertyToPage`|指定したプロパティの処理を可能にするプロパティ ページの CLSID を返します。|  
|`GetPredefinedStrings`|指定したプロパティが使用するための有効な値の説明を示します \(文字列`LPOLESTR` のポインター\) のカウントが設定された配列を返します。|  
|`SetPredefinedValue`|トークン `dwCookie.`によって識別される定義済みの値にプロパティの値を設定します|  
  
## 要件  
 ヘッダー: dbgprop.h