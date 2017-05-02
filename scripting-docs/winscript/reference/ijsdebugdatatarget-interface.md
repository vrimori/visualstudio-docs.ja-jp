---
title: "IJsDebugDataTarget インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget インターフェイス
デバッガーによって実装されており、対象のデバッガー プロセスの状態にアクセスして変更する機能を提供します。  
  
## 構文  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## メンバー  
  
### パブリック メソッド  
  
|Name|Description|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory メソッド](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Reserves and\/or commits a region of memory within the virtual address space of the target process.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator メソッド](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|スタック フレームの列挙子を作成します。|  
|[IJsDebugDataTarget::FreeVirtualMemory メソッド](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|ターゲット プロセスの仮想アドレス空間内のメモリ領域を解放\/デコミットします。|  
|[IJsDebugDataTarget::GetThreadContext メソッド](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|指定したスレッドのコンテキストを取得します。|  
|[IJsDebugDataTarget::GetTlsValue メソッド](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|スレッドがデバッグ中の場合は、スレッド ローカル ストレージ \(TLS\) スロット内の値を、指定したインデックスに基づいて取得します。|  
|[IJsDebugDataTarget::ReadBSTR メソッド](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Reads a BSTR from the debug target.|  
|[IJsDebugDataTarget::ReadMemory メソッド](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Reads the memory of the target process.|  
|[IJsDebugDataTarget::ReadNullTerminatedString メソッド](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Reads the specified number of characters from the target.|  
|[IJsDebugDataTarget::WriteMemory メソッド](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Reads the memory of the target process.|  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)