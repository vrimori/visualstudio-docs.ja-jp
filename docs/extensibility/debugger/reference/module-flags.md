---
title: "MODULE_FLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2dcd4b4d63942d7c2f94eda558ea491fa7a1e57e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
 モジュールを指定しません。  
  
 MODULE_FLAG_SYSTEM  
 システム モジュールを指定します。  
  
 MODULE_FLAG_SYMBOLS  
 シンボルのモジュールを指定します。  
  
 MODULE_FLAG_64BIT  
 64 ビット モジュールを指定します。  
  
 MODULE_FLAG_OPTIMIZED  
 モジュールが最適化されているを指定します。 この状態が反映、**モジュール**ウィンドウです。  
  
 MODULE_FLAG_UNOPTIMIZED  
 モジュールが最適化されていないことを指定します。 この状態が反映、**モジュール**ウィンドウです。 これは、既定の状態です。  
  
## <a name="remarks"></a>コメント  
 使用、`m_dwModuleFlags`のメンバー、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)構造体。  
  
 これらのフラグは、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)