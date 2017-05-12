---
title: "IJsDebugDataTarget::ReadNullTerminatedString メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadNullTerminatedString メソッド
指定した数の文字をターゲットから読み取ります。  
  
## 構文  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### パラメーター  
 `address`  
 \[in\] The address to read from.  
  
 `characterSize`  
 \[入力\] 文字列の各文字のサイズ。  
  
 `maxCharacters`  
 \[入力\] 読み取る文字の最大数。maxCharacters は妥当な値であることが必要です。  128 MB を超えるメモリを要求するような値を指定すると、エラーが発生します。文字列が maxCharacters の文字数を超えた場合、結果の文字列でその超えた部分は切り捨てられます。  
  
 `pString`  
 \[出力\] ターゲットから読み取った BSTR。  
  
## 戻り値  
  
## 解説  
 切り捨てられた場合は S\_FALSE を返します。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)