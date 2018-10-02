---
title: DEBUG_REASON |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 883630e7c9e00a58eac143a6cde7ee40109bb4e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47549106"
---
# <a name="debugreason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DEBUG_REASON](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-reason)します。  
  
デバッグ プロセスを起動した理由を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 特定できないエラーが発生しました (このとして提供される既定の条件を合わせる上の理由から、もう一方のいずれの場合)。  
  
 DEBUG_REASON_USER_LAUNCHED  
 ユーザーの要求プロセスが開始されました。  
  
 DEBUG_REASON_USER_ATTACHED  
 既に実行中のプロセスは、ユーザーに関連付けられました。  
  
 DEBUG_REASON_AUTO_ATTACHED  
 プロセスが起動したときに自動的にアタッチします。  
  
 DEBUG_REASON_CAUSALITY  
 プロセスを起動したために、*ジャスト イン タイム*(JIT) デバッグ イベント。  
  
## <a name="remarks"></a>Remarks  
 返される、 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

