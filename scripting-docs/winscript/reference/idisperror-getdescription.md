---
title: "IDispError::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetDescription
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetDescription"
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetDescription
エラーのテキスト説明を返します。  
  
## 構文  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### パラメーター  
 `pbstrDescription`  
 \[入力\]エラーの簡単な説明を含むを文字列です。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 テキストはエラーが検出されたメソッドの `IDispatchEx::InvokeEx` に渡されたロケール識別子 \(LCID\) で指定された言語で返されます。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## 参照  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)