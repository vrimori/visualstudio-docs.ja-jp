---
title: IDebugCoreServer2::GetMachineUtilities_V7 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 265c5b414c53fb6dfe43f63c1016204b8ff02c81
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908666"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
このメソッドは、サーバーのマシン ユーティリティを取得します。  
  
> [!NOTE]
>  このメソッドは廃止されています。 使用しないでください ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]は常に返します`E_NOTIMPL`このメソッドが呼び出された場合)。 これは歴史的な理由から保持されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppUtil`  
 [out]返します、`IDebugMDMUtil2_V7`マシン ユーティリティの情報を表すインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 常に返します`E_NOTIMPL`メソッドが実装されていないことを示します。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 常に返します`E_NOTIMPL`場合、このメソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)