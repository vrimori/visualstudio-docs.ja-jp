---
title: IDebugMemoryBytes2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a7c7dbc966c6c2747de4c969975ef8455cf6b0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116859"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
このインターフェイスは、メモリのバイト数を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、メモリ内のバイトを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)システム メモリへのアクセスを提供するには、このインターフェイスを返します。 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)と[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)オブジェクトのバイトへのアクセスを提供するには、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugMemoryBytes2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|指定された位置から始まるバイト シーケンスを読み取ります。|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|書き込みます`dwCount`(バイト単位) を開始位置として`pStartContext`です。|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|このインターフェイスによって表されるメモリのバイト単位のサイズを取得します。|  
  
## <a name="remarks"></a>コメント  
 プロパティの場合、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)配列を表すインターフェイスを提供、`IDebugMemoryBytes2`その配列内の値にアクセスするインターフェイスです。  
  
 Visual Studio の**メモリ ビュー**呼び出し[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)を取得する、`IDebugMemoryBytes2`システム メモリにアクセスするためのインターフェイスです。 アクセスできるアドレスが取得されたメモリのビューに、アドレスとして入力された式を解析しを使用して、解析された式の評価によって[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)を取得する、`IDebugProperty2`インターフェイスです。 呼び出し[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)を返します、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)メモリ アドレスを記述します。 このメモリに渡されるコンテキスト[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)と[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)