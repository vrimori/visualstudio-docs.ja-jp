---
title: PROVIDER_FIELDS |Microsoft Docs
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
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d8e332974859693cab75c5345f7ec6b03548d8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843965"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

プログラムのプロバイダーに関連付けられたプロパティを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 `ProgramNodes`フィールドは有効です。  
  
 PFIELD_IS_DEBUGGER_PRESENT  
 `fIsDebuggerPresent`フィールドは有効です。  
  
## <a name="remarks"></a>Remarks  
 これらの値が返されます、`Fields`のメンバー、 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)を構造体のどのフィールドが入力された明示的に示すために構造体。  
  
 これらの値は、演算と組み合わせることができます`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)

