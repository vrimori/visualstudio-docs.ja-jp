---
title: IDebugProgram2::GetProgramId |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 17101ce15fba12a066005dfdb51c7162a6df60d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910050"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
このプログラムの GUID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pguidProgramId`  
 [out]返します、`GUID`このプログラムにします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 デバッグ エンジン (DE) は、最初に渡されたプログラム id を返す必要があります、 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)または[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッド。 これにより、プログラムの識別デバッガーの間でのコンポーネント。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)