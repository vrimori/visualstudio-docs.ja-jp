---
title: "TYPE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TYPE_INFO"
helpviewer_keywords: 
  - "TYPE_INFO 構造体"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造体はさまざまな種類のフィールドの種類に関する情報を指定します。  
  
## 構文  
  
```cpp#  
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
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### パラメーター  
 dwKind  
 共用体を解釈する方法を決定 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) の列挙体の値。  
  
 type.typeMeta  
 \[C\+\+\] `dwKind` のみが `TYPE_KIND_METADATA` 場合 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 構造を設定します。  
  
 type.typePdb  
 \[C\+\+\] `dwKind` のみが `TYPE_KIND_PDB` 場合 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 構造を設定します。  
  
 type.typeBuilt  
 \[C\+\+\] `dwKind` のみが `TYPE_KIND_BUILT` 場合 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) 構造を設定します。  
  
 type.unused  
 未使用の埋め込み。  
  
 type  
 共用体の名前。  
  
 unionmember  
 \[C\#\] `dwKind` のみに基づいて適切な構造体の型にマーシャリングします。  
  
## 解説  
 この構造が表示される [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) のメソッドに渡されます。  構造体の内容がどのように解釈されるか `dwKind` のフィールドに基づいています。  
  
> [!NOTE]
>  `dwKind` が `TYPE_KIND_BUILT` と等しい場合のみ\[C\+\+\] `TYPE_INFO` の構造を破棄するとき [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) の基になるオブジェクトを解放する必要があります。  これは `typeInfo.type.typeBuilt.pUnderlyingField->Release()` を呼び出してされます。  
  
 \[C\# のみそれぞれの型の `unionmember` のメンバーを解釈する方法\] 次の表に示します。  これは1 種類の種類用にする方法の例を次に示します。  
  
|`dwKind`|`unionmember` は型として解釈します|  
|--------------|------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## 使用例  
 この例ではC\# の `TYPE_INFO` の構造体の `unionmember` のメンバーをデコードする方法を示します。  この例では1 種類だけ \(\)`TYPE_KIND_METADATA` 解釈する例では同じとして解釈されます。  
  
```c#  
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
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)