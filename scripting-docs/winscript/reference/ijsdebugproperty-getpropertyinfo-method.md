---
title: "IJsDebugProperty::GetPropertyInfo メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProperty.GetPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: ab9d6e0b-0448-4f21-b0b0-1738867587d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProperty::GetPropertyInfo メソッド
このオブジェクトの情報を取得します。  
  
## 構文  
  
```  
HRESULT GetPropertyInfo(  
   UINT nRadix,  
   JsDebugPropertyInfo *pPropertyInfo  
);  
```  
  
#### パラメーター  
 `nRadix`  
 \[入力\] 使用する基数。  
  
 `pPropertyInfo`  
 \[出力\] オブジェクトに関する情報。  
  
## 戻り値  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugProperty インターフェイス](../../winscript/reference/ijsdebugproperty-interface.md)