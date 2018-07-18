---
title: IDebugCodeContext2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b46ec36a93ac91647a3f17aac28187519ca2447
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103878"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
このインターフェイスは、コードの命令の開始位置を表します。 ほとんどのランタイム アーキテクチャ今日では、コード コンテキストできますと見なすプログラムの実行のストリーム内のアドレス。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、ドキュメントの位置にコードの命令の位置を関連付けるには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 多くのインターフェイスのメソッドが最も一般的に、このインターフェイスを返す[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)です。 使用広範で、 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)ブレークポイント解決情報と同様にも使用するインターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|アクティブなコードのコンテキストに対応するドキュメントのコンテキストを取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|このコードのコンテキストの言語情報を取得します。|  
  
## <a name="remarks"></a>コメント  
 主な違い、`IDebugCodeContext2`インターフェイスおよび[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)インターフェイスは、`IDebugCodeContext2`命令配置は常にします。 つまり、`IDebugCodeContext2`が常に、命令の先頭を指している一方、`IDebugMemoryContext2`ランタイム アーキテクチャでは、メモリのすべてのバイトを指す場合があります。 `IDebugCodeContext2` 基本的なストレージのサイズ (通常はバイト単位) ではなく、命令がインクリメントされます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)