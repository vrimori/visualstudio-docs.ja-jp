---
title: Ijsdebug::openvirtualprocess メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093991"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess メソッド
新しい仮想プロセス オブジェクトの作成に使用するファクトリ メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `processId`  
 [入力] デバッガーをアタッチするプロセス ID。  
  
 `runtimeJsBaseAddress`  
 [入力] JavaScript ランタイムがターゲット プロセスに読み込まれるベース アドレス。  
  
 `pDataTarget`  
 [入力] プロセスの状態を照会するために使用するデバッガーに付属のインターフェイス。  
  
 `ppProcess`  
 [出力] 新しいデバッグ プロセス オブジェクト。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>Remarks  
 Jscript9diag と Jscript9 が一致しない場合は E_JsDEBUG_MISMATCHED_RUNTIME を返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebug インターフェイス](../../winscript/reference/ijsdebug-interface.md)