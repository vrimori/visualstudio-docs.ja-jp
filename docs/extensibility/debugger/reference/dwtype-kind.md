---
title: "dwTYPE_KIND |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: dwTYPE_KIND
helpviewer_keywords: dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5207bbb9ff81a274d60ffb5957d2b5f31c73dbf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)として共用体を解釈するか、 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)構造体。  
  
 TYPE_KIND_PDB  
 `TYPE_INFO`として共用体を解釈するか、 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)構造体。  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO`として共用体を解釈するか、 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)構造体。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値に表示されます、`dwKind`のフィールド、 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)構造体を使用して、解釈する方法、`type`共用体のメンバーです。 `TYPE_INFO`への呼び出しによって返される構造体、 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)