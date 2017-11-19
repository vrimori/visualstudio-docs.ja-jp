---
title: "IDebugProcess3::GetENCAvailableState |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::GetENCAvailableState
helpviewer_keywords: IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86fc95def355c3483fae02b8e9f909aaadfd44f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
このメソッドは、プロセスの現在のエディット コンティニュの状態を取得します。 カスタム ポートのサプライヤーを常に返します`E_NOTIMPL`です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```csharp  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pReason`  
 [out]値、 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列挙します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  カスタム ポートのサプライヤーを常に返します`E_NOTIMPL`です。  
  
## <a name="remarks"></a>コメント  
 この状態の影響を受けました[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)