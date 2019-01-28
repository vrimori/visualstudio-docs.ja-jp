---
title: BP_RESOLUTION_LOCATION |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 295fc99fcaaaf784c4055922407e69cbf2856dbf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985173"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
ブレークポイント解像度の位置の構造を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>メンバー  
 `bpType`  
 値、 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)を解釈する方法を指定する列挙体、 `bpResLocation` union または`unionmemberX`メンバー。  
  
 `bpResLocation.bpresCode`  
 [C++ のみ]含まれています、 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)場合構造体`bpType`  = `BPT_CODE`します。  
  
 `bpResLocation.bpresData`  
 [C++ のみ]含まれています、 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)場合構造体`bpType`  = `BPT_DATA`します。  
  
 `bpResLocation.unused`  
 [C++ のみ]プレース ホルダー。  
  
 `unionmember1`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember2`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember3`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
 `unionmember4`  
 [C#のみ]解釈する方法については、「解説」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 この構造体のメンバーである、 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)と[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)構造体。  
  
 [C#のみ]`unionmemberX`メンバーは、次の表に従って解釈されます。 左の列を確認、`bpType`間で各を決定する値、`unionmemberX`マーシャ リングおよびメンバーを表します、`unionmemberX`それに応じて。 C# では、この構造を解釈する方法の例を参照してください。  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (データ式)|`string` (関数名)|`string` (イメージ名)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>例  
 この例では、解釈、`BP_RESOLUTION_LOCATION`構造 (C#)。  
  
```csharp  
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)