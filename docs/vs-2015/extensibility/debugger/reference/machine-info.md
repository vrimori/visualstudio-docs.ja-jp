---
title: MACHINE_INFO |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42fcd2df1e09209717e76297e91eb065c3bc495c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540307"
---
# <a name="machineinfo"></a>MACHINE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[MACHINE_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/machine-info)します。  
  
特定のコンピューターについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

