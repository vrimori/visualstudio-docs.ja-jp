---
title: EVALFLAGS |Microsoft Docs
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
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd387423d8f548b454c232794055e0f4c1194ad3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204510"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

式の評価を制御するフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 存在する場合は、戻り値に評価することを指定します。  
  
 EVAL_NOSIDEEFFECTS  
 副作用を許可しないことを指定します。  
  
 EVAL_ALLOWBPS  
 ブレークポイントの停止を指定します。  
  
 EVAL_ALLOWERRORREPORT  
 エラー報告を許可するホストを指定します。 主に、Internet Explorer でスクリプトに式の評価に使用します。  
  
 EVAL_FUNCTION_AS_ADDRESS  
 関数を呼び出す代わりに、アドレスとして評価される関数を強制的にします。  
  
 EVAL_NOFUNCEVAL  
 関数が評価するを防ぎます。 たとえば、`int`式トークン`myExpression(int) + 10`します。 この関数は、アドレスとしてではない値を正しく評価できます。  
  
 EVAL_NOEVENTS  
 セッション デバッグ マネージャー (SDM) または、IDE には式の評価中に発生するイベントを送信しないかを示すフラグです。  
  
## <a name="remarks"></a>Remarks  
 これらのフラグは、引数として渡される、 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)と[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)メソッド。  
  
 これらのフラグは、ビットごとの OR と組み合わせることがあります。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

