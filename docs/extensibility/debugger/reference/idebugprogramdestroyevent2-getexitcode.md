---
title: IDebugProgramDestroyEvent2::GetExitCode |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramDestroyEvent2::GetExitCode
helpviewer_keywords:
- IDebugProgramDestroyEvent2::GetExitCode
ms.assetid: 7f540cf6-e2d1-42b0-913e-a26d654b7659
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f20f2bfdd8106ba09c5b1de60f7df556d0c0c211
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114853"
---
# <a name="idebugprogramdestroyevent2getexitcode"></a>IDebugProgramDestroyEvent2::GetExitCode
プログラムの終了コードを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExitCode(   
   DWORD* pdwExit  
);  
```  
  
```csharp  
int GetExitCode(   
   out uint pdwExit  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwExit`  
 [out]プログラムの終了コードを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)