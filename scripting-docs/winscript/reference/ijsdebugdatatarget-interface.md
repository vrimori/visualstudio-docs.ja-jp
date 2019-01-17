---
title: IJsDebugDataTarget インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e14046443ca0560deacb6ddb6e39b1fc25d18fea
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097423"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget インターフェイス
デバッガーによって実装されており、対象のデバッガー プロセスの状態にアクセスして変更する機能を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory メソッド](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|ターゲット プロセスの仮想アドレス空間内のメモリ領域を予約/コミットします。|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator メソッド](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|スタック フレームの列挙子を作成します。|  
|[IJsDebugDataTarget::FreeVirtualMemory メソッド](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|ターゲット プロセスの仮想アドレス空間内のメモリ領域を解放/デコミットします。|  
|[IJsDebugDataTarget::GetThreadContext メソッド](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|指定したスレッドのコンテキストを取得します。|  
|[IJsDebugDataTarget::GetTlsValue メソッド](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|スレッドがデバッグ中の場合は、スレッド ローカル ストレージ (TLS) スロット内の値を、指定したインデックスに基づいて取得します。|  
|[IJsDebugDataTarget::ReadBSTR メソッド](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|デバッグ対象から BSTR を読み取ります。|  
|[IJsDebugDataTarget::ReadMemory メソッド](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|ターゲット プロセスのメモリを読み取ります。|  
|[IJsDebugDataTarget::ReadNullTerminatedString メソッド](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|指定した数の文字をターゲットから読み取ります。|  
|[IJsDebugDataTarget::WriteMemory メソッド](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|ターゲット プロセスのメモリを読み取ります。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)