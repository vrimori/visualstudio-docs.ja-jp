---
title: "IDebugReference2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2
helpviewer_keywords: IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 30f3b8351789adbb52651909cf9ff3b669934d66
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreference2"></a>IDebugReference2
このインターフェイスは、スタック フレームのプロパティまたはその他のいくつかのプロパティへの参照を表します。  
  
> [!NOTE]
>  `IDebugReference2`将来使用して、そのメソッドが返す必要がありますすべてに予約されている`E_NOTIMPL`です。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、特定の種類の値への参照を表すためには、このインターフェイスを実装します。 たとえば、値では、数値式の評価、メモリ、またはレジスタとその値の一覧を表示するためのメモリ コンテキストの結果として可能性があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)このインターフェイスを取得します。 [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)と[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)このインターフェイスを返すこともできます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugReference2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|取得、 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)この参照を記述する構造体。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|この参照文字列からの値を設定します。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|この参照を別の参照からの値を設定します。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|この参照の子を列挙します。|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|このリファレンスの親を取得します。|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|この参照の参照を最も多く派生を取得します。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|この参照が参照するメモリのバイト数を取得します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|このリファレンスのメモリのコンテキストを取得します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|このリファレンスのバイト単位のサイズを取得します。|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|この参照型を設定します。|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|他のこの参照を比較します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  この"property"の使用する必要がありますと混同しない、つまり、クラスのメンバー変数が、`IDebugReference2`そのエンティティを表すことができます。  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 、プロパティを表すときに`IDebugReference2`、デバッグ中のプログラム内のオブジェクトへの参照を通常のプロパティの参照を表します。  
  
 プロパティとの参照の主な違いは、名前のないインスタンスを参照中に、プロパティが、オブジェクトの名前付きインスタンスを指すことです。 によって、プログラムのヒープのオブジェクトにプロパティは参照など、`"a.b"`です。 同じオブジェクトを別のプロパティは参照`"c.d"`です。 このプロパティを参照する方法では、する必要があります`"a.b"`または`"c.d"`スコープ内にあります。 この同じオブジェクトへの参照が無名です。オブジェクトは、そのオブジェクトのメモリが有効な場合に限りを参照できます。  
  
 `IDebugProperty2`名前、型、およびアドレスの値としてのインターフェイスを考えることができます。 `IDebugReference2`、別のに対して、型、およびアドレスと見なすことができます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)