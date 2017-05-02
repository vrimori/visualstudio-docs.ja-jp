---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
本質的に見ることができない返されたテキスト、プロパティを説明する名前、呼び出し元のユーザー インターフェイスに表示できる、表示型に文字列を取得します。  
  
## 構文  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### パラメーター  
 `dispid`  
 \[入力\]表示名が必要なプロパティの識別子をディスパッチします。  
  
 `pBstr`  
 \[入力\] `dispID`で指定されるプロパティの表示名を含む `BSTR` へのポインター。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 解説  
 返される文字列は、プロパティの有効値ではありません。  また、プロパティの、文字列表示です。  
  
## 参照  
 [IPerPropertyBrowsing2 インターフェイス](../../winscript/reference/iperpropertybrowsing2-interface-1.md)