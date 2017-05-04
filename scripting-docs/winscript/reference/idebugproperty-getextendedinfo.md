---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
プロパティの情報が拡張されます。  
  
## 構文  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### パラメーター  
 `cInfos`  
 \[入力\]拡張情報の計算を追加します。  
  
 `rgguidExtendedInfo`  
 \[入力\] `GUID`の配列は拡張情報の複数の項目を同時に取得できるように渡されます。  
  
 `pExtendedInfo`  
 \[入力\]拡張プロパティの情報を取得するために使用できる `VARIANT`の配列を返します。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 解説  
 このインターフェイスはこのオブジェクトの情報が拡張されます。  API は `IDebugProperty::GetPropertyInfo`を使用して取得してから提供された\) 情報を取得するためだけに存在します。  
  
## 参照  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)