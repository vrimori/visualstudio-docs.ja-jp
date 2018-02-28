---
title: "CANSTOP_REASON |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98b1e4a9db18490079dd443cb296481aed64376a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="canstopreason"></a>CANSTOP_REASON
プログラムが実行の特定のポイントに到達した後の実行を停止するかどうかを判断するために使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>メンバー  
 CANSTOP_ENTRYPOINT  
 指定されたプログラムのエントリ ポイントを指定します。  
  
 CANSTOP_STEPIN  
 関数にステップ インを指定します。  
  
## <a name="remarks"></a>コメント  
 引数として渡される、 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)セッション デバッグ マネージャー (SDM) がプログラムのエントリ ポイントに到達した後、または関数またはメソッドにステップ インした後を停止する場合をことを確認します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)