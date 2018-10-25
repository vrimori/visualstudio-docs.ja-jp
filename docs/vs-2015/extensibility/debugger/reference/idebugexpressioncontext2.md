---
title: IDebugExpressionContext2 |Microsoft Docs
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
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b58a8b2987b8ad90cad0fa3655ee9fed751f1877
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181793"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、式の評価のコンテキストを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、式を評価できるコンテキストを表すには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) this を返しますインターフェイス。 このインターフェイスは、デバッグ中のプログラムが一時停止されているし、スタック フレームは、使用可能な場合にのみアクセスできます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugExpressionContext2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|評価コンテキストの名前を取得します。|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|評価のためのテキスト ベースの式を解析します。|  
  
## <a name="remarks"></a>Remarks  
 評価コンテキストは、式の評価を実行するためのスコープとして考えることができます。  
  
 セッション デバッグ マネージャー (SDM) がへの呼び出しで DE からスタック フレームを取得するプログラムが停止されると、 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)します。 SDM を呼び出して[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)を取得する、`IDebugExpressionContext2`インターフェイス。 これがへの呼び出しに続く[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)を作成する、 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)インターフェイスで、すぐに評価できる解析された式を表します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)

