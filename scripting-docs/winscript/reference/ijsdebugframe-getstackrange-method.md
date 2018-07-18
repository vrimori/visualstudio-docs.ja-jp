---
title: Ijsdebugframe::getstackrange メソッド |Microsoft ドキュメント
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
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727872"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange メソッド
論理的な JavaScript スタック フレームの絶対アドレス範囲を返します。  
  
## <a name="syntax"></a>構文  
  
```  
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
  
## <a name="remarks"></a>コメント  
 このメソッドは、複数のランタイムから収集されインタリーブ化されたスタック トレースを統合する場合に役立ちます。 開始日、終了のスタック ポインターは、(JavaScript ランタイムの解釈されたフレーム) 用の複数の物理マシン スタック フレームを囲んでいることができます。 開始 > 大きくなるにつれて、スタック高から低アドレスを終了します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)