---
title: CONTEXT_INFO_FIELDS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 712876c38996b0e9b5f0b65cf0b0269d43b15907
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028434"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
メモリのコンテキストを取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>メンバー  
 CIF_MODULEURL  
 初期化/使用、`bstrModuleUrl`のフィールド、 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)構造体。  
  
 CIF_FUNCTION  
 初期化/使用、`bstrFunction`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_FUNCTIONOFFSET  
 初期化/使用、`posFunctionOffset`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_ADDRESS  
 初期化/使用、`bstrAddress`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_ADDRESSOFFSET  
 初期化/使用、`bstrAddressOffset`のフィールド、`CONTEXT_INFO`構造体。  
  
 CIF_ALLFIELDS  
 すべてのフィールドの初期化/使用して、`CONTEXT_INFO`構造体。  
  
## <a name="remarks"></a>Remarks  
 これらの値がパラメーターに渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)のどのフィールドを示すメソッド、 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)構造体が初期化されるは。  
  
 これらのフラグは、のどのフィールドを示すためにも使用、`CONTEXT_INFO`構造が返されるときに構造体が使用し、無効です。  
  
 これらの値は、ビットごとの OR と組み合わせることがあります。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)