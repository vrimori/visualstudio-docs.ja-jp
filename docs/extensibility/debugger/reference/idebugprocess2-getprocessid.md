---
title: IDebugProcess2::GetProcessId |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a643e980e0a0d03b6c6d2634890dc5aba61b1f8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869094"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
このプロセスの GUID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pguidProcessId`  
 [out]このプロセスの GUID を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 グローバル一意識別子 (GUID) は、システムで実行されているその他のすべてのプロセスからこのプロセスを識別します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)