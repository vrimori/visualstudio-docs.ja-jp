---
title: IDebugStackFrame::GetLanguageString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc20c3ce2f5d198e167b83ffddb65cedc84402d7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087738"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
言語の短い、または時間の長いテキストの説明を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fLong`  
 [in]フラグは、場所`TRUE`長い説明を返しますと`FALSE`短い説明を返します。  
  
 `pbstrLanguage`  
 [out]言語の説明です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 通常場合、`fLong`は`FALSE`、このメソッドは、スタック フレームに関連付けられている言語の名前のみを提供します。 ときに`fLong`は`TRUE`、このメソッドは、完全な製品の説明を提供可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame インターフェイス](../../winscript/reference/idebugstackframe-interface.md)