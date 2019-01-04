---
title: BPRESI_FIELDS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bad42049bf10b3b5e0f599ea5b043dd73cabc051
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931516"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
ブレークポイントの解決について取得する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>メンバー  
 BPRESI_BPRESLOCATION  
 初期化/使用、 `bpResLocation` (ブレークポイント解像度の位置) フィールドの[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)構造体。  
  
 BPRESI_PROGRAM  
 初期化/使用、`pProgram`のフィールド、`BP_RESOLUTION_INFO`構造体。  
  
 BPRESI_THREAD  
 初期化/使用、`pThread`のフィールド、`BP_RESOLUTION_INFO`構造体。  
  
 BPRESI_ALLFIELDS  
 すべてのフィールドを指定します。  
  
## <a name="remarks"></a>Remarks  
 渡される、 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)のどのフィールドを示すメソッド、 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)構造体が初期化されるは。  
  
 これらのフラグは、のどのフィールドを示すためにも使用、`BP_RESOLUTION_INFO`構造体が返されるときに構造体が使用し、無効です。  
  
 これらの値は、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)