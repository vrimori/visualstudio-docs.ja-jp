---
title: IDebugMemoryBytes2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a9434f7464d4c13d0c4085a3ad195ba8b1bd2f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007582"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
このインターフェイスは、メモリのバイト数を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、メモリ内のバイトを表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)システム メモリへのアクセスを提供するには、このインターフェイスを返します。 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)と[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)オブジェクトのバイトへのアクセスを提供するには、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugMemoryBytes2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|指定した位置から始まるバイト シーケンスを読み取ります。|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|書き込みます`dwCount`で始まるバイト`pStartContext`します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|このインターフェイスによって表されるメモリのバイト単位のサイズを取得します。|  
  
## <a name="remarks"></a>Remarks  
 プロパティの場合、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)配列を表すインターフェイスを提供します、`IDebugMemoryBytes2`その配列内の値にアクセスするインターフェイス。  
  
 Visual Studio の**メモリ ビュー**呼び出し[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)を取得する、`IDebugMemoryBytes2`システム メモリにアクセスするためのインターフェイス。 アクセスできるアドレスを取得、メモリのビューに、アドレスとして入力された式を解析し、使用して、解析された式を評価して[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)を取得する、`IDebugProperty2`インターフェイス。 呼び出し[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)を返します、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)メモリ アドレスを記述します。 このメモリ コンテキストに渡されます[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)と[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)