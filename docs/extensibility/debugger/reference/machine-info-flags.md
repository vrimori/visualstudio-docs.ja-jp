---
title: MACHINE_INFO_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO_FLAGS
helpviewer_keywords:
- MACHINE_INFO_FLAGS enumeration
ms.assetid: 1482095d-9a2e-4ef1-9e14-362c0b85194e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a3b9e8877ff77048f2b7dd697fc57971ddaf6e7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915415"
---
# <a name="machineinfoflags"></a>MACHINE_INFO_FLAGS
マシンの記述に使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_MACHINE_INFO_FLAGS {   
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001  
};  
typedef DWORD MACHINE_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FLAGS {   
   MCIFLAG_TERMINAL_SERVICES_AVAILABLE = 0x00000001  
};  
```  
  
## <a name="members"></a>メンバー  
 MCIFLAG_TERMINAL_SERVICES_AVAILABLE  
 ターミナル サービスが使用できることを示します。  
  
## <a name="remarks"></a>Remarks  
 として使用される、`Flags`のメンバー、 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)構造体。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)