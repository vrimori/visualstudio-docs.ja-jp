---
title: "IJsDebugDataTarget::FreeVirtualMemory メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::FreeVirtualMemory メソッド
Releases and\/or decommits a region of memory within the virtual address space of the target process.  
  
## 構文  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### パラメーター  
 `address`  
 \[入力\] メモリを解放する必要があるターゲット プロセス内のアドレス。  
  
 `size`  
 \[入力\] デコミットするバイト数。  メモリ領域を解放するには、この値をゼロにする必要があります。  
  
 `freeType`  
 \[入力\] 実行する解放操作の種類を指定します。  通常は MEM\_RELEASE \(0x8000\) であり、指定したページ領域を解放します。  この操作の後、ページは空き状態になります。  代わりに MEM\_DECOMMIT \(0x4000\) を使用すると、ページを解放せずにデコミットできます。  
  
## 戻り値  
  
## 解説  
 詳細については、「VirtualFree Win32 API」を参照してください。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)