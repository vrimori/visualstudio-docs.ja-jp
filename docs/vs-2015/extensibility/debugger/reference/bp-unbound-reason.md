---
title: BP_UNBOUND_REASON |Microsoft Docs
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
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d6060753a3208fd09485a52d0959daf31f6c3e0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250667"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ブレークポイントがバインドされた理由を説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>メンバー  
 BPUR_UNKNOWN  
 不明な理由です。  
  
 BPUR_CODE_UNLOADED  
 ブレークポイントを含むコードがアンロードされました。  
  
 BPUR_BREAKPOINT_REBIND  
 ブレークポイントが別の場所にバインドされています。 編集後に発生したり、ブレークポイントに移動したとき、またはファイル パスが無効になっているブレークポイントがバインドされている場合は、操作を続行します。  
  
 BPUR_ BREAKPOINT_ERROR  
 ブレークポイントを判定して、バインド後にエラーが発生されます。 これは管理対象のブレークポイント条件を持つは無効になります。  
  
## <a name="remarks"></a>Remarks  
 によって返される、 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)

