---
title: "IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::MapPropertyToPage"
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::MapPropertyToPage
このプロパティを編集するために使用できるプロパティ ページの CLSID を返します。  
  
## 構文  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### パラメーター  
 `dispid`  
 \[入力\]目的のプロパティの識別子をディスパッチします。  
  
 `pClsidPropPage`  
 \[入力\]プロパティに関連付けられたプロパティ ページの CLSID を識別するへのポインター。  このメソッドが失敗した場合、\*`pClsidPropPage` は CLSID\_NULL に設定されます。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IPerPropertyBrowsing2 インターフェイス](../../winscript/reference/iperpropertybrowsing2-interface-1.md)