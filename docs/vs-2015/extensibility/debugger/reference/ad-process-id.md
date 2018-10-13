---
title: AD_PROCESS_ID |Microsoft Docs
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
- AD_PROCESS_ID
helpviewer_keywords:
- AD_PROCESS_ID union
ms.assetid: 4cb40d12-2e92-4f09-83f4-689928bd65b3
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c573683ddde6199e8a9c0f1e8802547d286a7aa0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277486"
---
# <a name="adprocessid"></a>AD_PROCESS_ID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

システム ID または GUID 可能性のあるプロセス ID を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
typedef struct _AD_PROCESS_ID {  
   AD_PROCESS_ID_TYPE ProcessIdType;  
   union {  
      DWORD dwProcessId;   
      GUID  guidProcessId;   
      DWORD dwUnused;   
   } ProcessId;  
} AD_PROCESS_ID;  
```  
  
```csharp  
public struct AD_PROCESS_ID {  
   AD_PROCESS_ID_TYPE ProcessIdType;  
   DWORD              dwProcessId;   
   GUID               guidProcessId;   
   DWORD              dwUnused;   
};  
```  
  
## <a name="members"></a>メンバー  
 `ProcessIdType`  
 値、 [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)を解釈する方法を指定する列挙体、`ProcessId`共用体 (または、マネージ コードの構造体のメンバーにアクセスする場合)。  
  
 dwProcessId  
 システムからの値としてプロセス ID。  
  
 guidProcessId  
 GUID としてプロセス ID。  
  
 dwUnused  
 余白。  
  
## <a name="remarks"></a>Remarks  
 この構造体は、次のメソッドに渡されます。  
  
-   [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)  
  
-   [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)  
  
-   [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
  
-   [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)  
  
 次のメソッドから返されます。  
  
-   [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
-   [GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)   
 [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [含ま](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

