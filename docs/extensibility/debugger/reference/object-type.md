---
title: "OBJECT_TYPE |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OBJECT_TYPE
helpviewer_keywords: OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 223833857568da64e24aa2e955ecabce0b36af57
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="objecttype"></a>OBJECT_TYPE
式エバリュエーターからのオブジェクトの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_OBJECT_TYPE {   
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
public enum enum_OBJECT_TYPE {   
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
 オブジェクトが 2 バイトの符号なし整数であることを示します。  
  
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
 オブジェクトが 8 バイト浮動小数点数であることを示します。  
  
 OBJECT_TYPE_OBJECT  
 オブジェクトがオブジェクトであることを示します。  
  
 OBJECT_TYPE_NULL  
 オブジェクトが NULL であることを示します。  
  
 OBJECT_TYPE_CLASS  
 オブジェクトが、クラスであることを示します。  
  
## <a name="remarks"></a>コメント  
 引数として渡される、 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)と[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)