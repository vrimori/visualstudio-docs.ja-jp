---
title: "PROCESS_INFO_FIELDS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b733bceec1b6408ba11be0e04a15e2d917b3f61a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
プロセスを取得する情報の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
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
public enum enum_PROCESS_INFO_FIELDS {   
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
 初期化/を使用して、`bstrFileName`のフィールド、 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造体。  
  
 PIF_BASE_NAME  
 初期化/を使用して、`bstrBaseName`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_TITLE  
 初期化/を使用して、`bstrTitle`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_PROCESS_ID  
 初期化/を使用して、`ProcessId`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_SESSION_ID  
 初期化/を使用して、`dwSessionId`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_ATTACHED_SESSION_NAME  
 初期化/を使用して、`bstrAttachedSessionName`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_CREATION_TIME  
 初期化/を使用して、`CreationTime`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_FLAGS  
 初期化/を使用して、`Flags`のフィールド、`PROCESS_INFO`構造体。  
  
 PIF_ALL  
 すべてのフィールドに入力します。  
  
## <a name="remarks"></a>コメント  
 渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)メソッドのどのフィールドを示すために、 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造が初期化するのには。  
  
 使用`Fields`のフィールド、`PROCESS_INFO`構造のどのフィールドが使用されていると有効なことを示します。  
  
 これらのフラグは、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)