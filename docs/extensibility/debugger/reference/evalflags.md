---
title: "EVALFLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVALFLAGS
helpviewer_keywords: EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 62b372daffee279c3e36efde53a8b002c8b9b73a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="evalflags"></a>EVALFLAGS
式の評価を制御するフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>メンバー  
 EVAL_RETURNVALUE  
 存在する場合は、戻り値を評価することを指定します。  
  
 EVAL_NOSIDEEFFECTS  
 副作用を許可しないことを指定します。  
  
 EVAL_ALLOWBPS  
 ブレークポイントで停止を指定します。  
  
 EVAL_ALLOWERRORREPORT  
 エラーが許可されるには、ホストにレポートを指定します。 主に、Internet Explorer でスクリプト内の式の評価に使用します。  
  
 EVAL_FUNCTION_AS_ADDRESS  
 関数を呼び出す代わりに、アドレスとして評価される関数を強制的に実行します。  
  
 EVAL_NOFUNCEVAL  
 関数が評価するを防ぎます。 たとえば、`int`トークン、式で`myExpression(int) + 10`です。 この関数は、値としてではなくが、アドレスとして正しく評価できます。  
  
 EVAL_NOEVENTS  
 式の評価中に発生するイベントがセッション デバッグ マネージャー (SDM) または IDE にいない送信することを示すフラグです。  
  
## <a name="remarks"></a>コメント  
 これらのフラグがへの引数として渡される、 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)と[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)メソッドです。  
  
 これらのフラグは、ビットごとの OR と組み合わせることがあります。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)