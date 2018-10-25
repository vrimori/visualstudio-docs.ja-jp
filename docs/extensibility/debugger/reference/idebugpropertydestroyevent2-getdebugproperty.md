---
title: IDebugPropertyDestroyEvent2::GetDebugProperty |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
helpviewer_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
ms.assetid: c96ae785-0ac8-4df4-8df3-15a8d7e13687
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8243b0bb04a8232a80ce80022c0ed6e188dc0e29
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823139"
---
# <a name="idebugpropertydestroyevent2getdebugproperty"></a>IDebugPropertyDestroyEvent2::GetDebugProperty
破棄するプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppProperty`  
 [out]返します、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)破棄するプロパティを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)