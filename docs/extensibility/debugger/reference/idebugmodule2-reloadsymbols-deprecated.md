---
title: IDebugModule2::ReloadSymbols_Deprecated |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 182561200e6239520b1345f43cc0a150baa30622
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961310"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
互換性のために残されています。 使用しないでください。 このモジュールのシンボルを再読み込みします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszUrlToSymbols`  
 [in]シンボル ストアへのパス。  
  
 `pbstrDebugMessage`  
 [out][モジュール] ウィンドウで、モジュール名の右側に表示されるステータスまたはエラー メッセージなどの情報メッセージを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 デバッグ エンジンは常に返す必要があります`E_FAIL`します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドはサポートされなくなりました。 実装、 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)メソッド代わりにします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)