---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IsEqualObject メソッド"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
オブジェクトが現在のオブジェクトと等しいかどうかを判定します。  
  
## 構文  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### パラメーター  
 `punk`  
 \[入力\]現在のオブジェクトと比較するオブジェクトのアドレス。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|オブジェクトは同等です。|  
|`S_FALSE`|オブジェクトは等価です。|  
  
## 解説  
 `IsEqualObject` のメソッドの実装は、オブジェクトが同じ場合にのみ `S_OK` を返す必要があります。  
  
## 参照  
 [IObjectIdentity インターフェイス](../../winscript/reference/iobjectidentity-interface.md)