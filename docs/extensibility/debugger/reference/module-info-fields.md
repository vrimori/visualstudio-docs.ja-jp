---
title: "MODULE_INFO_FIELDS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d96175501d0e75ee1949847c69909c23a3b08582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
モジュールのデバッグ情報のフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>メンバー  
 MIF_NONE  
 すべての構造体にフィールドを初期化するか、/使用します。  
  
 MIF_NAME  
 初期化/を使用して、`m_bstrName`フィールドで、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)構造体。  
  
 MIF_URL  
 初期化/を使用して、`m_bstrUrl`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_VERSION  
 初期化/を使用して、`m_bstrVersion`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_DEBUGMESSAGE  
 初期化/を使用して、`m_bstrDebugMessage`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_LOADADDRESS  
 初期化/を使用して、`m_addrLoadAddress`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_PREFFEREDADDRESS  
 初期化/を使用して、`m_addrPreferredLoadAddress`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_SIZE  
 初期化/を使用して、`m_dwSize`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_LOADORDER  
 初期化/を使用して、`m_dwLoadOrder`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_TIMESTAMP  
 初期化/を使用して、`m_TimeStamp`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_URLSYMBOLLOCATION  
 初期化/を使用して、`m_bstrUrlSymbolLocation`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_FLAGS  
 初期化/を使用して、`m_dwModuleFlags`フィールドで、`MODULE_INFO`構造体。  
  
 MIF_ALLFIELDS  
 すべてのフィールドの初期化/使用、`MODULE_INFO`構造体。  
  
## <a name="remarks"></a>コメント  
 これらの値が引数として渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)メソッドのどのフィールドを示すために、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)構造が初期化するのには。  
  
 これらの値はでも使用、`MODULE_INFO`構造のどのフィールドが使用されていると有効なことを示します。  
  
 これらのフラグは、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)