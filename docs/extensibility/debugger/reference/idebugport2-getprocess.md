---
title: IDebugPort2::GetProcess |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4958e296e83e3de0d8c3e41b73c0b30af144d743
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863205"
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
指定されたポートで実行されているプロセスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProcess(   
   AD_PROCESS_ID    ProcessId,  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(   
   AD_PROCESS_ID      ProcessId,  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ProcessId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)プロセス識別子を指定する構造体。  
  
 `ppProcess`  
 [out]返します、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)プロセスを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)