---
title: IDebugStackFrame2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efa6c917e5a59c291d07757b52fab4fe8aa7b0ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
このインターフェイスは、特定のスレッドのコール スタックの 1 つのスタック フレームを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、スタック フレームを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)を取得する、 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)インターフェイスです。 呼び出す[次](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)を取得する、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)を含む構造体、`IDebugStackFrame2`インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugStackFrame2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|このスタック フレームのコードのコンテキストを取得します。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|このスタック フレームのドキュメントのコンテキストを取得します。|  
|[getName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|スタック フレームの名前を取得します。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|スタック フレームの説明を取得します。|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|スタック フレームに関連付けられている物理アドレスの範囲のコンピューターに依存する形式を取得します。|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|スタック フレームおよびスレッドの現在のコンテキストで式の評価を行うための評価コンテキストを取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|スタック フレームに関連する言語を取得します。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|スタック フレームに関連付けられているプロパティの説明を取得します。|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|列挙子のスタック フレームのプロパティを作成します。|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|スタック フレームに関連付けられているスレッドを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、デバッグ中のプログラムが (いずれかの原因となったユーザー セット ブレークポイントまたは例外によって) ブレークポイントで停止された場合にのみ取得されます。 このインターフェイスから式を評価する式のコンテキストを取得することができます、レジスタの一覧を返すことが、または呼び出し履歴を取得して調べることができます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)