---
title: CANSTOP_REASON |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba5f493303fd3b667e51bcd1f71a02d35c8fbc6f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963061"
---
# <a name="canstopreason"></a>CANSTOP_REASON
プログラムが実行の特定のポイントに到達した後の実行を停止するかどうかを判断するために使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>メンバー  
 CANSTOP_ENTRYPOINT  
 特定のプログラムのエントリ ポイントを指定します。  
  
 CANSTOP_STEPIN  
 関数にステップ インを指定します。  
  
## <a name="remarks"></a>Remarks  
 引数として渡される、 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)セッション デバッグ マネージャー (SDM) の場合は、プログラムのエントリ ポイントに到達した後、または関数またはメソッドにステップ インした後に停止しても問題をことを確認します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)