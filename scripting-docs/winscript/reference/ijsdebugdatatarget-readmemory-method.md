---
title: "IJsDebugDataTarget::ReadMemory メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadMemory メソッド
Reads the memory of the target process.  
  
## 構文  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### パラメーター  
 `address`  
 \[入力\] ターゲット プロセスのメモリの読み取り元となるベース アドレス。  
  
 `flags`  
 \[入力\] ReadMemory の動作を制御するフラグ。  
  
 `pBuffer`  
 \[出力\] ターゲット プロセスのアドレス空間の内容を受け取るバッファー。  エラーが発生した場合、このバッファーの内容は未指定になります。  
  
 `size`  
 \[入力\] プロセスから読み取るバイト数。  
  
 `pBytesRead`  
 \[出力\] ターゲット プロセスから読み取られたバイト数。  JsDebugAllowPartialRead を指定しない場合、正常に終了すると、この値は常に入力サイズと等しくなります。  JsDebugAllowPartialRead を指定した場合、正常に終了すると、この値はゼロより大きくなります。  
  
## 戻り値  
  
## 解説  
 正常に終了した場合は S\_OK を返し、エラーが発生した場合はエラー コードが使用されます。  Returns E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS if the address is not valid.  詳細については、「JsDebugAllowPartialRead」を参照してください。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)