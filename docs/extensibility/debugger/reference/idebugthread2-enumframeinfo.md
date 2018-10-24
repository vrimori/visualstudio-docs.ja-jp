---
title: IDebugThread2::EnumFrameInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98cd9db7785d7d7867e48f0bd56a2f5ab657a344
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942758"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
このスレッドのスタック フレームの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFieldSpec`  
 [in]フラグの組み合わせ、 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)のどのフィールドを指定する列挙体、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造は、入力します。指定、`FIF_FUNCNAME_FORMAT`関数名を 1 つの文字列に書式設定フラグ。  
  
 `nRadix`  
 [in]列挙子の数値情報を書式設定に使用する基数。  
  
 `ppEnum`  
 [out]返します、 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)オブジェクトの一覧を含む[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)スタック フレームを記述する構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 スレッドのフレームは、最初に列挙する現在のフレームと最後に列挙された最も古いフレームを順に列挙されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)