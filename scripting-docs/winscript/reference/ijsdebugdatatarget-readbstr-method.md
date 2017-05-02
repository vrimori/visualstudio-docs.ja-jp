---
title: "IJsDebugDataTarget::ReadBSTR メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadBSTR メソッド
デバッグ対象から BSTR を読み取ります。  
  
## 構文  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### パラメーター  
 `address`  
 \[入力\] 読み取り元のアドレス。  
  
 `pString`  
 \[出力\] デバッグ対象から読み取った BSTR。  
  
## 戻り値  
  
## 解説  
 アドレスが有効でない場合は E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS を返します。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)