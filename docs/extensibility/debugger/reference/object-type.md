---
title: OBJECT_TYPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df0b3d6ef73b81f005fbdac82f8dc3faa5601fba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941359"
---
# <a name="objecttype"></a>OBJECT_TYPE
式エバリュエーターからオブジェクトの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>メンバー  
 OBJECT_TYPE_BOOLEAN  
 オブジェクトがブール値であることを示します。  
  
 OBJECT_TYPE_CHAR  
 オブジェクトが文字であることを示します。  
  
 OBJECT_TYPE_I1  
 オブジェクトが 1 バイトの符号付き整数であることを示します。  
  
 OBJECT_TYPE_U1  
 オブジェクトが 1 バイトの符号なし整数であることを示します。  
  
 OBJECT_TYPE_I2  
 オブジェクトが 2 バイト符号付き整数であることを示します。  
  
 OBJECT_TYPE_U2  
 オブジェクトが 2 バイト符号なし整数であることを示します。  
  
 OBJECT_TYPE_I4  
 オブジェクトが 4 バイト符号付き整数であることを示します。  
  
 OBJECT_TYPE_U4  
 オブジェクトが 4 バイト符号なし整数であることを示します。  
  
 OBJECT_TYPE_I8  
 オブジェクトが 8 バイト符号付き整数であることを示します。  
  
 OBJECT_TYPE_U8  
 オブジェクトが 8 バイト符号なし整数であることを示します。  
  
 OBJECT_TYPE_R4  
 オブジェクトが 4 バイト浮動小数点数であることを示します。  
  
 OBJECT_TYPE_R8  
 オブジェクトが 8 バイトの浮動小数点数であることを示します。  
  
 OBJECT_TYPE_OBJECT  
 オブジェクトがオブジェクトであることを示します。  
  
 OBJECT_TYPE_NULL  
 オブジェクトが NULL であることを示します。  
  
 OBJECT_TYPE_CLASS  
 オブジェクトがクラスであることを示します。  
  
## <a name="remarks"></a>Remarks  
 引数として渡される、 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)と[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)