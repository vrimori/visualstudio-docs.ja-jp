---
title: "IDispError::GetHresult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHresult
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHresult"
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHresult
`IDispError` のオブジェクトからエラー コードを取得します。  
  
## 構文  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### パラメーター  
 `phr`  
 \[入力\]エラー コードを指定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは `IDispError` のオブジェクトからエラー コードを取得します。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## 参照  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)