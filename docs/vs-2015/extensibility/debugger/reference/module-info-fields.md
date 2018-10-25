---
title: MODULE_INFO_FIELDS |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 249bb62aaf2801626415ab56625f250640a8d28e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866065"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

モジュールのデバッグ情報のフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 構造体のフィールドの [なし] を初期化するか、/使用します。  
  
 MIF_NAME  
 初期化/使用、`m_bstrName`フィールドに、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)構造体。  
  
 MIF_URL  
 初期化/使用、`m_bstrUrl`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_VERSION  
 初期化/使用、`m_bstrVersion`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_DEBUGMESSAGE  
 初期化/使用、`m_bstrDebugMessage`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_LOADADDRESS  
 初期化/使用、`m_addrLoadAddress`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_PREFFEREDADDRESS  
 初期化/使用、`m_addrPreferredLoadAddress`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_SIZE  
 初期化/使用、`m_dwSize`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_LOADORDER  
 初期化/使用、`m_dwLoadOrder`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_TIMESTAMP  
 初期化/使用、`m_TimeStamp`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_URLSYMBOLLOCATION  
 初期化/使用、`m_bstrUrlSymbolLocation`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_FLAGS  
 初期化/使用、`m_dwModuleFlags`フィールドに、`MODULE_INFO`構造体。  
  
 MIF_ALLFIELDS  
 すべてのフィールドの初期化/使用、`MODULE_INFO`構造体。  
  
## <a name="remarks"></a>Remarks  
 これらの値が引数として渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)のどのフィールドを示すメソッド、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)構造体が初期化されるは。  
  
 これらの値が使用されることも、`MODULE_INFO`フィールドが使用し、有効なときは、構造体。  
  
 これらのフラグは、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)

