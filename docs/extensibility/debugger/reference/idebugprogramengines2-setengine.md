---
title: IDebugProgramEngines2::SetEngine |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66861a6af435d1c26657cc37f73995c80f1c005f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985527"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
プログラムまたはプログラムのノードにするデバッグ エンジンを使用してこのプログラムをデバッグするには、(DE) を指示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```csharp  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidEngine`  
 [in]デの GUID です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)