---
title: GUID_ARRAY |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96313333c330bff1a278a81e1276f8bcd2799e21
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017878"
---
# <a name="guidarray"></a>GUID_ARRAY
使用可能なデバッグ エンジンの一意の識別子の配列について説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagGUID_ARRAY  
{  
   DWORD dwCount;  
   GUID *Members;  
} GUID_ARRAY;  
```  
  
```csharp  
public struct GUID_ARRAY  
{  
   public uint dwCount;  
   public Guid Members;  
}  
```  
  
## <a name="terms"></a>用語  
 dwCount  
 配列内の一意の識別子の数。  
  
 メンバー  
 一意の識別子を含む配列。  
  
## <a name="remarks"></a>Remarks  
 この構造体がによって返される、 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)