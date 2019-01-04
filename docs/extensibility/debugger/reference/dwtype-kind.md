---
title: dwTYPE_KIND |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d350b429b86c9ab3082816605c4c79e56982bb5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988233"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
型を解釈する方法を指定します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 TYPE_KIND_METADATA  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)共用体として解釈する必要があります、 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)構造体。  
  
 TYPE_KIND_PDB  
 `TYPE_INFO`共用体として解釈する必要があります、 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)構造体。  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO`共用体として解釈する必要があります、 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)構造体。  
  
## <a name="remarks"></a>Remarks  
 この列挙体の値に表示されます、`dwKind`のフィールド、 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)構造体し、解釈する方法を決定するために使用、`type`共用体メンバーです。 `TYPE_INFO`への呼び出しによって返される構造体、 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)