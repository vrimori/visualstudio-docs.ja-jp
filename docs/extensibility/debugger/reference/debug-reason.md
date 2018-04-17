---
title: DEBUG_REASON |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47cfd171d23420396c6d7ab5416db32cc05511f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debugreason"></a>DEBUG_REASON
デバッグ プロセスを起動した理由を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 DEBUG_REASON_ERROR  
 特定できないエラーが発生しました (このとして使用される既定の条件合わせる上の理由によりの他の場合)。  
  
 DEBUG_REASON_USER_LAUNCHED  
 プロセスがユーザーの要求で起動されました。  
  
 DEBUG_REASON_USER_ATTACHED  
 既に実行中のプロセスにアタッチされているユーザーがします。  
  
 DEBUG_REASON_AUTO_ATTACHED  
 プロセスが起動したときに自動的にアタッチします。  
  
 DEBUG_REASON_CAUSALITY  
 理由のため、プロセスを起動した、*ジャスト イン タイム*(JIT) デバッグ イベント。  
  
## <a name="remarks"></a>コメント  
 返される、 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)