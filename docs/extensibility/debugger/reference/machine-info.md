---
title: MACHINE_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ee759f1b7a69c6813f48eeceb2e962effb1bfe6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986389"
---
# <a name="machineinfo"></a>MACHINE_INFO
特定のコンピューターについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>メンバー  
 `Fields`  
 フラグの組み合わせ、 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)構造体のフィールドが初期化されるかを指定する列挙体。  
  
 `bstrName`  
 コンピューター名。 呼び出しに相当[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)します。  
  
 `Flags`  
 フラグの組み合わせ、 [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)マシン属性を説明する列挙体。  
  
## <a name="remarks"></a>Remarks  
 この構造体が呼び出しによって返される、 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)