---
title: PROVIDER_PROCESS_DATA |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 789385ae229214beeb6c2ab9be90a964127e5e13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819733"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
この構造体は、コンピューターで実行されているプロセスに関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>メンバー  
 フィールド  
 フラグの組み合わせ、 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)どのフィールドに入力を示す、列挙体。  
  
 ProgramNodes  
 A [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)プログラム ノードの配列を含む構造体。  
  
 fIsDebuggerPresent  
 0 以外の場合 (`TRUE`) 場合、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッガーが実行されている、ゼロ (`FALSE`) でない場合。  
  
## <a name="remarks"></a>Remarks  
 この構造体に渡される、 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)メソッドでいっぱいになった場所。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)