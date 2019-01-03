---
title: IDebugEngine2::SetLocale |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6881a217ba1d5db885c8c963885eb69e4257b26e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908411"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
デバッグ エンジン (DE) のロケールを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wLangID`  
 [in]言語ロケールを指定します。 たとえば、英語の場合は 1033 です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドはセッション デバッグ マネージャー (SDM) に、DE によって返される文字列が正しくローカライズできるように、IDE のロケール設定を継承します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)