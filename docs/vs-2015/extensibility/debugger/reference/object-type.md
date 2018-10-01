---
title: OBJECT_TYPE |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1cd02a49a92eefae129e53322b005760733e0417
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535776"
---
# <a name="objecttype"></a>OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[OBJECT_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/object-type)します。  
  
式エバリュエーターからオブジェクトの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="requirements"></a>要件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

