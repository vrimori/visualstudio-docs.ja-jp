---
title: IDebugProperty2 |Microsoft Docs
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
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63b39e45d73be47538263b7e7cd5ce1e12769f95
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215645"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、スタック フレームのプロパティ、プログラムのドキュメント プロパティ、またはその他のいくつかのプロパティを表します。 プロパティは、通常は、式の評価の結果です。  
  
> [!NOTE]
>  この「プロパティ」を使用する必要がありますと混同しない、つまり、クラスのメンバー変数が、`IDebugProperty2`そのエンティティを表すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、特定の種類の値を表すためには、このインターフェイスを実装します。 たとえば、値は、式の評価、メモリ、またはレジスタとその値の一覧を表示するためのメモリのコンテキストの結果として数値。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)評価の結果を表す、このインターフェイスを取得します。 `IDebugExpression2::EvaluateAsync` 送信することによってこのインターフェイスを返します、 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)インターフェイスを呼び出して、SDM を[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)プロパティを取得します。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)関連付けられているスクリプト ドキュメントを提供するには、このインターフェイスを返します。  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)関数の戻り値を表すためには、このインターフェイスを返します。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)メモリ コンテキスト名など、プログラムのさまざまなプロパティを表すには、このインターフェイスを返します。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)スタック フレームのローカル変数などのさまざまなプロパティを表すには、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProperty2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|入力、 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)プロパティを記述する構造体。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|文字列からプロパティの値を設定します。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|指定された参照の値から、プロパティの値を設定します。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|プロパティの子を列挙します。|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|プロパティの親を返します。|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|プロパティのほとんど派生プロパティを説明するプロパティを返します。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|プロパティの値を構成するメモリのバイトを返します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|メモリ コンテキスト プロパティ値を返します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|プロパティの値のバイト単位のサイズを返します。|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|このプロパティの値への参照を返します。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|拡張プロパティの情報を返します。|  
  
## <a name="remarks"></a>Remarks  
 プロパティによって表される、`IDebugProperty2`インターフェイス、名前、種類、およびアドレスの値として考えることができます。 一般的な用語で、`IDebugProperty2`を持つ親と子ノードの階層構造を表すことができます。  
  
 プロパティは、通常は一時的なもの、たとえば継続時間だけ現在のスタック フレーム。 その一方で、参照によって表される、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)インターフェイスの場合は、値がメモリに残っている限り継続します。  
  
 IDE を使用できる、`IDebugProperty2`ユーザー参照および実行時にプロパティを変更できるようにするインターフェイス。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

