---
title: Ijsdebugdatatarget::gettlsvalue メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f81e9ea6cca9bf54753a496e07903d23bb913fc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095330"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue メソッド
スレッドがデバッグ中の場合は、スレッド ローカル ストレージ (TLS) スロット内の値を、指定したインデックスに基づいて取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `threadId`  
 [入力] 読み取り元となるターゲット プロセスで実行中のスレッド。  
  
 `tlsIndex`  
 [入力] ターゲット プロセスが TlsAlloc 関数を呼び出したときに割り当てられた TLS インデックス。  
  
 `pValue`  
 [出力] スレッドの TLS スロットに格納されたポインター サイズの値。 対象のスレッドが 32 ビットの場合、この値の上位 32 ビットがゼロになります。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>Remarks  
 プロセスの各スレッドには TLS インデックスごとに専用のスロットがあります。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)