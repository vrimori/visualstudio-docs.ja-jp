---
title: "Ijsdebugdatatarget::freevirtualmemory メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory メソッド
ターゲット プロセスの仮想アドレス空間内のメモリ領域を解放/デコミットします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [入力] メモリを解放する必要があるターゲット プロセス内のアドレス。  
  
 `size`  
 [入力] デコミットするバイト数。 メモリ領域を解放するには、この値をゼロにする必要があります。  
  
 `freeType`  
 [入力] 実行する解放操作の種類を指定します。 通常は MEM_RELEASE (0x8000) であり、指定したページ領域を解放します。 この操作の後、ページは空き状態になります。 代わりに MEM_DECOMMIT (0x4000) を使用すると、ページを解放せずにデコミットできます。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 詳細については、「VirtualFree Win32 API」を参照してください。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)