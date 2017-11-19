---
title: "Ijsdebugdatatarget::readmemory メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory メソッド
ターゲット プロセスのメモリを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [入力] ターゲット プロセスのメモリの読み取り元となるベース アドレス。  
  
 `flags`  
 [入力] ReadMemory の動作を制御するフラグ。  
  
 `pBuffer`  
 [出力] ターゲット プロセスのアドレス空間の内容を受け取るバッファー。 エラーが発生した場合、このバッファーの内容は未指定になります。  
  
 `size`  
 [入力] プロセスから読み取るバイト数。  
  
 `pBytesRead`  
 [出力] ターゲット プロセスから読み取られたバイト数。 JsDebugAllowPartialRead を指定しない場合、正常に終了すると、この値は常に入力サイズと等しくなります。 JsDebugAllowPartialRead を指定した場合、正常に終了すると、この値はゼロより大きくなります。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 正常に終了した場合は S_OK を返し、エラーが発生した場合はエラー コードが使用されます。 アドレスが有効でない場合は E_JsDEBUG_INVALID_MEMORY_ADDRESS を返します。 詳細については、「JsDebugAllowPartialRead」を参照してください。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)