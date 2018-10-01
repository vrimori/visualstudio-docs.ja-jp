---
title: IDebugProcess3::GetENCAvailableState |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: caee81d16d12e3d428b7b6ecc0ccab2663775610
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537265"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProcess3::GetENCAvailableState](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess3-getencavailablestate)します。  
  
このメソッドは、プロセスの現在のエディット コンティニュの状態を取得します。 カスタム ポート サプライヤーが常に返す必要があります`E_NOTIMPL`します。  
  
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
 [out]値、 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  カスタム ポート サプライヤーが常に返す必要があります`E_NOTIMPL`します。  
  
## <a name="remarks"></a>Remarks  
 この状態は影響を受ける[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

