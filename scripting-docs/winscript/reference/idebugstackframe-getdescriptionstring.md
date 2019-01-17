---
title: IDebugStackFrame::GetDescriptionString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f6479485a508f71797d6965f71edd3253927088
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097228"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
スタック フレームの短い、または時間の長いテキストの説明を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fLong`  
 [in]フラグは、場所`TRUE`長い説明を返しますと`FALSE`短い説明を返します。  
  
 `pbstrDescription`  
 [out]スタック フレームの説明です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 通常場合、`fLong`は`FALSE`、このメソッドは、スタック フレームに関連付けられている関数の名前のみを提供します。 ときに`fLong`は`TRUE`、このメソッドは可能性があります、関数パラメーターおよび他の関連情報も提供します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame インターフェイス](../../winscript/reference/idebugstackframe-interface.md)