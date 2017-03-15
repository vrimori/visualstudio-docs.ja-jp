---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "OBJECT_TYPE 列挙型"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

式エバリュエーターのオブジェクトの種類を指定します。  
  
## 構文  
  
```cpp#  
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
  
```c#  
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
  
## メンバー  
 OBJECT\_TYPE\_BOOLEAN  
 オブジェクトがブール値であることを示します。  
  
 OBJECT\_TYPE\_CHAR  
 オブジェクトが文字であることを示します。  
  
 OBJECT\_TYPE\_I1  
 オブジェクトがバイトの符号付き整数であることを示します。  
  
 OBJECT\_TYPE\_U1  
 オブジェクトがバイトの符号なし整数であることを示します。  
  
 OBJECT\_TYPE\_I2  
 オブジェクトは2 バイトの符号付き整数であることを示します。  
  
 OBJECT\_TYPE\_U2  
 オブジェクトは2 バイトの符号なし整数であることを示します。  
  
 OBJECT\_TYPE\_I4  
 オブジェクトは4 バイトの符号付き整数であることを示します。  
  
 OBJECT\_TYPE\_U4  
 オブジェクトは4 バイトの符号なし整数であることを示します。  
  
 OBJECT\_TYPE\_I8  
 オブジェクトがバイトの符号付き整数であることを示します。  
  
 OBJECT\_TYPE\_U8  
 オブジェクトがバイトの符号なし整数であることを示します。  
  
 OBJECT\_TYPE\_R4  
 オブジェクトが 4 バイト浮動小数点数であることを示します。  
  
 OBJECT\_TYPE\_R8  
 オブジェクトがバイトの浮動小数点数であることを示します。  
  
 OBJECT\_TYPE\_OBJECT  
 オブジェクトがオブジェクトであることを示します。  
  
 OBJECT\_TYPE\_NULL  
 オブジェクトが null であることを示します。  
  
 OBJECT\_TYPE\_CLASS  
 オブジェクトはクラスであることを示します。  
  
## 解説  
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) と [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) のメソッドに引数として渡されます。  
  
## 必要条件  
 ヘッダー : ee.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)