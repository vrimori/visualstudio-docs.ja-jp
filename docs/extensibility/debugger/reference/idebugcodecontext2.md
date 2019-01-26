---
title: IDebugCodeContext2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac77b0c43d6b300bd41e0b49d4b523dc0f43d025
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990408"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
このインターフェイスは、コードの命令の開始位置を表します。 ほとんどのランタイム アーキテクチャの今日では、コードのコンテキストできます見なすことがプログラムの実行のストリーム内のアドレス。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジンでは、ドキュメントの位置にコード命令の位置を関連付けるには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 多くのインターフェイスのメソッドは通常、このインターフェイスを返す[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)します。 組み合わせて広範に使用したことも、 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)ブレークポイント解像度の情報のようにも使用するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|アクティブなコードのコンテキストに対応するドキュメントのコンテキストを取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|このコードのコンテキストの言語情報を取得します。|  
  
## <a name="remarks"></a>Remarks  
 主な違い、`IDebugCodeContext2`インターフェイスと[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)インターフェイスは、`IDebugCodeContext2`命令配置は常にします。 つまり、`IDebugCodeContext2`一方、命令の場合の先頭を指すことが常に、`IDebugMemoryContext2`ランタイム アーキテクチャのメモリのすべてのバイトを指すこともできます。 `IDebugCodeContext2` 基本的なストレージ サイズ (通常はバイト) ではなく、命令がインクリメントされます。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)