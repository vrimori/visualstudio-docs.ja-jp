---
title: "IPerPropertyBrowsing2::SetPredefinedValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.SetPredefinedValue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::SetPredefinedValue"
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::SetPredefinedValue
`dispID`で指定されるプロパティの値を設定します。  定義済みの値はトークン `dwCookie.`で識別されます。  
  
## 構文  
  
```  
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### パラメーター  
 `dispid`  
 \[入力\]定義済みの値が設定されるプロパティの識別子をディスパッチします。  
  
 `dwCookie`  
 \[入力\]セットに値を識別するトークン。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IPerPropertyBrowsing2 インターフェイス](../../winscript/reference/iperpropertybrowsing2-interface-1.md)