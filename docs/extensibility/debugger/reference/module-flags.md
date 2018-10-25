---
title: MODULE_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 89dbb562dfbab83f56664aad7fdd107ea9d0e397
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873982"
---
# <a name="moduleflags"></a>MODULE_FLAGS
モジュールの記述に使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>メンバー  
 MODULE_FLAG_NONE  
 モジュールは指定されません。  
  
 MODULE_FLAG_SYSTEM  
 システム モジュールを指定します。  
  
 MODULE_FLAG_SYMBOLS  
 シンボルのモジュールを指定します。  
  
 MODULE_FLAG_64BIT  
 64 ビット モジュールを指定します。  
  
 MODULE_FLAG_OPTIMIZED  
 モジュールが最適化されているを指定します。 この状態が反映、**モジュール**ウィンドウ。  
  
 MODULE_FLAG_UNOPTIMIZED  
 モジュールが最適化されていないことを指定します。 この状態が反映、**モジュール**ウィンドウ。 これは、既定の状態です。  
  
## <a name="remarks"></a>Remarks  
 使用、`m_dwModuleFlags`のメンバー、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)構造体。  
  
 これらのフラグは、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)