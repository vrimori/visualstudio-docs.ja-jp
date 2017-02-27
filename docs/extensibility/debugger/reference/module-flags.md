---
title: "MODULE_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "MODULE_FLAGS 列挙型"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

モジュールを記述するために使用します。  
  
## 構文  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## メンバー  
 MODULE\_FLAG\_NONE  
 モジュールを指定しません。  
  
 MODULE\_FLAG\_SYSTEM  
 システムのモジュールを指定します。  
  
 MODULE\_FLAG\_SYMBOLS  
 シンボルのモジュールを指定します。  
  
 MODULE\_FLAG\_64BIT  
 64 ビット モジュールを指定します。  
  
 MODULE\_FLAG\_OPTIMIZED  
 最適化されたモジュールを指定します。  この状態は ENT0ENT \[出力\] ウィンドウに反映されます。  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 最適化されていないモジュールを指定します。  この状態は ENT0ENT \[出力\] ウィンドウに反映されます。  これが既定の状態です。  
  
## 解説  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) の構造体のメンバー `m_dwModuleFlags` に使用されます。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)