---
title: Ijsdebugframe::getstackrange メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 049be8a665dae396d4e92fe847e757b266dc6025
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090286"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange メソッド
論理的な JavaScript スタック フレームの絶対アドレス範囲を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStart`  
 [出力] フレームの末尾のスタック ポインター。  
  
 `pEnd`  
 [出力] フレームの先頭のスタック ポインター。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、複数のランタイムから収集されインタリーブ化されたスタック トレースを統合する場合に役立ちます。 先頭、末尾のスタック ポインターにはことができます (解釈された JavaScript ランタイム フレーム) の複数の物理マシン スタック フレームが含まれます。 開始 > スタックが高から低位アドレスへ拡大に合わせてを終了します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)