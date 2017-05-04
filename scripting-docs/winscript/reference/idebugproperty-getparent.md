---
title: "IDebugProperty::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetParent"
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetParent
プロパティの親プロパティを取得します。  
  
## 構文  
  
```  
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### パラメーター  
 `ppParent`  
 \[入力\]プロパティの親を表す `IDebugProperty` のインターフェイスを返します。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)