---
title: PROCESS_INFO_FIELDS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 75a323690ef11e31a8d738e8042b2b6fab7a7fc0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891334"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
プロセスを取得する情報の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>メンバー  
 PIF_FILE_NAME  
 初期化/使用、`bstrFileName`のフィールド、 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造体。  
  
 PIF_BASE_NAME  
 初期化/使用、`bstrBaseName`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_TITLE  
 初期化/使用、`bstrTitle`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_PROCESS_ID  
 初期化/使用、`ProcessId`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_SESSION_ID  
 初期化/使用、`dwSessionId`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_ATTACHED_SESSION_NAME  
 初期化/使用、`bstrAttachedSessionName`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_CREATION_TIME  
 初期化/使用、`CreationTime`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_FLAGS  
 初期化/使用、`Flags`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_ALL  
 すべてのフィールドに入力します。  
  
## <a name="remarks"></a>Remarks  
 渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)のどのフィールドを示すメソッド、 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造体が初期化されるは。  
  
 使用`Fields`のフィールド、`PROCESS_INFO`フィールドが使用し、有効なときは、構造体。  
  
 これらのフラグは、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)