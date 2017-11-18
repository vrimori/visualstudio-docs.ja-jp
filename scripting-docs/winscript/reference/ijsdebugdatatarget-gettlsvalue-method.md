---
title: "Ijsdebugdatatarget::gettlsvalue メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue メソッド
スレッドがデバッグ中の場合は、スレッド ローカル ストレージ (TLS) スロット内の値を、指定したインデックスに基づいて取得します。  
  
## <a name="syntax"></a>構文  
  
```  
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
  
## <a name="remarks"></a>コメント  
 プロセスの各スレッドには TLS インデックスごとに専用のスロットがあります。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)