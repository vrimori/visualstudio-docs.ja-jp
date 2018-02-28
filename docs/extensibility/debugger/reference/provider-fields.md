---
title: "PROVIDER_FIELDS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5fa01ee5eefcd8cc476abe0ce5fc512dd2191403
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="providerfields"></a>PROVIDER_FIELDS
プログラムの提供に関連付けられたプロパティを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```csharp  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## <a name="members"></a>メンバー  
 PFIELD_PROGRAM_NODES  
 `ProgramNodes`フィールドは無効です。  
  
 PFIELD_IS_DEBUGGER_PRESENT  
 `fIsDebuggerPresent`フィールドは無効です。  
  
## <a name="remarks"></a>コメント  
 これらの値が返されます、`Fields`のメンバー、 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)構造体のフィールドが入力に明示的に指定する構造体。  
  
 これらの値をビット単位と組み合わせて`OR`です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)