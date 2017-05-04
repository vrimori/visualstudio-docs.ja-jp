---
title: "IJsDebugDataTarget::AllocateVirtualMemory メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::AllocateVirtualMemory メソッド
ターゲット プロセスの仮想アドレス空間内のメモリ領域を予約\/コミットします。  
  
## 構文  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### パラメーター  
 `address`  
 \[入力\] メモリをコミット\/予約する必要があるターゲット プロセス内のアドレス。  この値は通常ゼロであり、その場合はシステムによってアドレスが選択されます。  
  
 `size`  
 \[入力\] 割り当てるメモリ領域のサイズ \(バイト単位\)。  システムによって次のページ境界に自動的に切り上げられます。  
  
 `allocationType`  
 \[入力\] 実行する割り当ての種類を指定します。  通常は MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\) であり、予約と割り当てを同時に行います。  
  
 `pageProtection`  
 \[入力\] 割り当てるページ領域のメモリ保護。  ページをコミットする場合は、メモリ保護定数 \(PAGE\_READWRITE、PAGE\_EXECUTE など\) のいずれかを指定できます。  
  
 `pAllocatedAddress`  
 \[出力\] 割り当てられたページ領域のベース アドレス。  
  
## 戻り値  
  
## 解説  
 この関数は、MEM\_RESET が使用されない限り、割り当てるメモリをゼロに初期化します。  詳細については、「VirtualAlloc Win32 API」を参照してください。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)