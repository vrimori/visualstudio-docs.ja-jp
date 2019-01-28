---
title: IDebugDocumentContext2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f648888e41557e7debe460d99c07cd1017150c0e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992296"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
このインターフェイスは、ソース ファイルのドキュメント内の位置を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、ソース コード レベルのデバッグのサポートの一部として、このインターフェイスを実装します。 ソース コード内の位置、だけでなくは、このインターフェイスは、コンテキストを比較して、ソース コード ドキュメント間を移動するためのメソッドを提供します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 最も一般的のいくつかのメソッドがインターフェイス、 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)と[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)インターフェイスは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDocumentContext2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|このドキュメントのコンテキストを含むドキュメントを取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|このドキュメントのコンテキストを含んでいるドキュメントの表示可能な名前を取得します。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|このドキュメントのコンテキストに関連付けられているすべてのコード コンテキストの一覧を取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|このドキュメントのコンテキストに関連付けられた言語を取得します。|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|このドキュメントのコンテキストのファイルのステートメントの範囲を取得します。|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|このドキュメントのコンテキストのソース範囲のファイルを取得します。|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|このドキュメントのコンテキスト ドキュメント コンテキストの指定した配列を比較します。|  
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|ステートメントまたは行の番号を指定して、ドキュメントのコンテキストに移動します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)