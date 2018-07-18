---
title: MODULE_INFO_FIELDS |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fcc6bd76a4a9aecade72347613ed4f36968c65eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125930"
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)