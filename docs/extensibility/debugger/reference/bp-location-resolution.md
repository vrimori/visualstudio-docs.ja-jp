---
title: BP_LOCATION_RESOLUTION |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_RESOLUTION
helpviewer_keywords:
- BP_LOCATION_RESOLUTION structure
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b93af8334e033f158763ae1d5e7d75ef9ae08967
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905481"
---
# <a name="bplocationresolution"></a>BP_LOCATION_RESOLUTION
特定の位置にブレークポイントの解決方法をについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BP_LOCATION_RESOLUTION {   
   IDebugBreakpointResolution2* pResolution;  
} BP_LOCATION_RESOLUTION;  
```  
  
## <a name="members"></a>メンバー  
 pResolution  
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)ブレークポイントとその解決策情報の種類を決定するオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 この構造体のメンバーである、 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)構造体、共用体の一部として。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)