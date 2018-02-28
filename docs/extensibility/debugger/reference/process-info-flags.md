---
title: "PROCESS_INFO_FLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9ff1df7e73c8f09934504552f33d7f9ce4c537e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
説明またはプロセスのプロパティを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>メンバー  
 PIFLAG_SYSTEM_PROCESS  
 プロセスがシステム プロセスであることを示します。  
  
 PIFLAG_DEBUGGER_ATTACHED  
 プロセスは、デバッガーによってデバッグされていることを示します。 ある可能性があります、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッガー、またはそれにいくつか他のデバッガー、WinDbg などの可能性があります。  
  
 PIFLAG_PROCESS_STOPPED  
 プロセスが停止していることを示します。 有効な場合にのみ`PIFLAG_DEBUGGER_ATTACHED`も指定されています。 使用できる[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]およびそれ以降。  
  
 PIFLAG_PROCESS_RUNNING  
 プロセスが実行されていることを示します。 有効な場合にのみ`PIFLAG_DEBUGGER_ATTACHED`も指定されています。 使用できる[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]およびそれ以降。  
  
## <a name="remarks"></a>コメント  
 使用、`Flags`のメンバー、 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造体。  
  
 これらのフラグは、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)