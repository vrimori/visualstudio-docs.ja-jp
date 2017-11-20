---
title: "AD_PROCESS_ID_TYPE |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AD_PROCESS_ID_TYPE
helpviewer_keywords: AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75904ef6e06ef7ccd6d126091f8ec0fbe523ac9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
プロセス ID を解釈する方法を指定します、 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)構造体。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>メンバー  
 AD_PROCESS_ID_SYSTEM  
 プロセス ID は、システム識別子です。 使用して、`ProcessId.dwProcessId`のフィールド、 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)構造体。  
  
 AD_PROCESS_ID_GUID  
 プロセス ID は GUID です。 使用して、`ProcessId.guidProcessId`のフィールド、`AD_PROCESS_ID`構造体。  
  
## <a name="remarks"></a>コメント  
 使用、`ProcessIdType`のメンバー、 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)構造に含まれているプロセス ID の種類を識別する構造体。 解釈する方法を決定、`ProcessId`共用体、構造体の。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)