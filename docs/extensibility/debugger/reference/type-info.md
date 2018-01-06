---
title: "TYPE_INFO |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TYPE_INFO
helpviewer_keywords: TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d6888d2680cffbde132885d730cd35f6e509c2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="typeinfo"></a>TYPE_INFO
この構造体では、さまざまな種類のフィールドの型に関する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 dwKind  
 値、 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)和集合を解釈する方法を決定する列挙です。  
  
 type.typeMeta  
 [C++ のみ]含まれています、 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)場合構造体`dwKind`は`TYPE_KIND_METADATA`します。  
  
 type.typePdb  
 [C++ のみ]含まれています、 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)場合構造体`dwKind`は`TYPE_KIND_PDB`します。  
  
 type.typeBuilt  
 [C++ のみ]含まれています、 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)場合構造体`dwKind`は`TYPE_KIND_BUILT`します。  
  
 type.unused  
 未使用のパディングです。  
  
 型  
 共用体の名前です。  
  
 unionmember  
 [C# の場合のみ]マーシャ リングに基づく適切な構造体の型にこの`dwKind`です。  
  
## <a name="remarks"></a>コメント  
 この構造体に渡される、 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)で塗り分けはメソッドです。 構造体の内容を解釈する方法がに基づいて、`dwKind`フィールドです。  
  
> [!NOTE]
>  [C++ のみ]場合`dwKind`equals `TYPE_KIND_BUILT`、基になるを解放する必要があるし、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)オブジェクトを破棄するとき、`TYPE_INFO`構造体。 これは、`typeInfo.type.typeBuilt.pUnderlyingField->Release()` を呼び出すことによって行われます。  
  
 [C# の場合のみ]次の表を解釈する方法を示しています、`unionmember`各種類の型のメンバーです。 この例では、1 つの種類の型にこれを行う方法を示します。  
  
|`dwKind`|`unionmember`として解釈されます。|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>例  
 この例を解釈する方法を示しています、`unionmember`のメンバー、 `TYPE_INFO` c# の構造体。 この例では、1 種類だけを解釈する (`TYPE_KIND_METADATA`) が、他のユーザーはまったく同じように解釈されます。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)