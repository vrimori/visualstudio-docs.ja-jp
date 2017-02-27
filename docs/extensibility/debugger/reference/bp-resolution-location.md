---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "BP_RESOLUTION_LOCATION 構造体"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントの解決の位置構造体を指定します。  
  
## 構文  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## メンバー  
 `bpType`  
 `unionmemberX` の `bpResLocation` または共用体のメンバーを解釈する方法を指定する [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) の列挙体の値。  
  
 `bpResLocation.bpresCode`  
 \[C\+\+\] [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) のみの構造を `bpType` \= `bpType``bpType``BPT_CODE` 含まれています。  
  
 `bpResLocation.bpresData`  
 \[C\+\+\] [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) のみの構造を `bpType` \= `bpType``bpType``BPT_DATA` 含まれています。  
  
 `bpResLocation.unused`  
 \[入力\] C\+\+ のみのプレースホルダー。  
  
 `unionmember1`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
 `unionmember2`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
 `unionmember3`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
 `unionmember4`  
 \[C\#\] を解釈する方法の解説を参照してください。  
  
## 解説  
 この構造は [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) と [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) の構造体のメンバーです。  
  
 \[C\#\] `unionmemberX` のみのメンバーを次の表に従って解釈されます。  `unionmemberX` の各メンバーが表す `unionmemberX` を確認しそれに応じてマーシャリングします。を確認するには左の列に `bpType` の値をポイントします。  C\# でこの構造を解釈する方法の例を参照してください。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string` データ \(式\)|`string` \(関数名\)|`string` \(イメージ名\)|`enum_BP_RES_DATA_FLAGS`|  
  
## 使用例  
 この例ではC\# の `BP_RESOLUTION_LOCATION` の構造を解釈する方法を示します。  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)