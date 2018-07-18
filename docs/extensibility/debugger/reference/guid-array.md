---
title: GUID_ARRAY |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1802d5784ad6e94aee4ff63fb51d2c92dbf164f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108415"
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
 配列の一意識別子の数です。  
  
 メンバー  
 一意の識別子を格納する配列。  
  
## <a name="remarks"></a>コメント  
 この構造体は、によって返される、 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)