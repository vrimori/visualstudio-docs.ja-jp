---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
`IDispError` で次のオブジェクトを取得します。  
  
## 構文  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### パラメーター  
 `ppde`  
 \[入力\] `IDispError` で次のオブジェクトを指定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは `IDispError` で次のオブジェクトを取得します。  これが `IDispError` の最後のオブジェクトの場合、このメソッドは、は無効になります。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## 参照  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)