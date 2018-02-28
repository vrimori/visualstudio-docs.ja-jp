---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a96a382c1dce73731fdd4326d8b0d1c35b7aa33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
現在のスレッドのスタック フレームの列挙子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwSpMin`  
 [in]アドレスの下限のスタック フレームを列挙します。  
  
 `ppedsf`  
 [out]現在のスレッドのスタック フレームの列挙子。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 スタック フレームの列挙子は、最後にプッシュされたフレームを使用して、スタックの上部で開始するフレームを返します。 列挙子より大きいまたは等しいアドレスを持つスタック フレームのみが含まれています。`dwSpMin`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrameSnifferEx インターフェイス](../../winscript/reference/idebugstackframesnifferex-interface.md)