---
title: Ijsdebugdatatarget::allocatevirtualmemory メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4eaf448e0be224f853674084a18f7aa2a6bd5ed7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086919"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory メソッド
ターゲット プロセスの仮想アドレス空間内のメモリ領域を予約/コミットします。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [入力] メモリをコミット/予約する必要があるターゲット プロセス内のアドレス。 この値は通常ゼロであり、その場合はシステムによってアドレスが選択されます。  
  
 `size`  
 [入力] 割り当てるメモリ領域のサイズ (バイト単位)。 システムによって次のページ境界に自動的に切り上げられます。  
  
 `allocationType`  
 [入力] 実行する割り当ての種類を指定します。 これは、通常は MEM_COMMIT &#124; MEM_RESERVE (0x3000) あり、予約し、1 つの手順で割り当てをコミットします。  
  
 `pageProtection`  
 [入力] 割り当てるページ領域のメモリ保護。 ページをコミットする場合は、メモリ保護定数 (PAGE_READWRITE、PAGE_EXECUTE など) のいずれかを指定できます。  
  
 `pAllocatedAddress`  
 [出力] 割り当てられたページ領域のベース アドレス。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>Remarks  
 この関数は、MEM_RESET が使用されない限り、割り当てるメモリをゼロに初期化します。 詳細については、「VirtualAlloc Win32 API」を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)