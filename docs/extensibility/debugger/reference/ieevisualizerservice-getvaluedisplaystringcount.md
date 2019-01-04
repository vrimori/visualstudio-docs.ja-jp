---
title: IEEVisualizerService::GetValueDisplayStringCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8af1b785e56d5efba2505b0cdbd5a9474b5c261b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957950"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
指定したプロパティまたはフィールドを表示する値の文字列の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `displayKind`  
 [in]値を[DisplayKind](../../../extensibility/debugger/reference/displaykind.md)列挙体。  
  
 `propertyOrField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)プロパティまたはフィールドを表すインターフェイスです。  
  
 `pcelt`  
 [out]表示する値の文字列の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)