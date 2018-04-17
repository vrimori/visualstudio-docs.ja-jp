---
title: BP_UNBOUND_REASON |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65398ac0c4bde18dc772d75ceea203bdbfe3b189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
ブレークポイントがバインドできなかった理由を説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 別の場所にブレークポイントを再バインドするとします。 編集の後に発生するでき、ブレークポイントに移動したとき、またはパスが無効になっているファイルにブレークポイントがバインドされている場合は、操作を続行できます。  
  
 BPUR_ BREAKPOINT_ERROR  
 ブレークポイントがバインドされている後にエラーが発生すると判断されます。 これはマネージ ブレークポイントの条件が無効になっています。  
  
## <a name="remarks"></a>コメント  
 によって返される、 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)