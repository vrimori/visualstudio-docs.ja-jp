---
title: IDebugDocumentContext2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 06ff06086c0f293f70af7d9570cf72df4be85608
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107700"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
このインターフェイスは、ソース ファイルのドキュメント内の位置を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、ソース コードのレベルのデバッグのサポートの一部としてこのインターフェイスを実装します。 ソース コード内の位置、に加えては、このインターフェイスは、コンテキストを比較して、ソース コード ドキュメントを移動するためのメソッドを提供します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 メソッドをいくつかのインターフェイスを最も一般的、 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)と[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)インターフェイスは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDocumentContext2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|このドキュメントのコンテキストを含むドキュメントを取得します。|  
|[getName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|このドキュメントのコンテキストを含むドキュメントの表示可能な名前を取得します。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|このドキュメントのコンテキストに関連付けられているすべてのコード コンテキストの一覧を取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|このドキュメントのコンテキストに関連付けられている言語を取得します。|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|このドキュメントのコンテキストのファイルのステートメントの範囲を取得します。|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|このドキュメントのコンテキストのファイルのソース範囲を取得します。|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|ドキュメントのコンテキストの指定した配列にこのドキュメントのコンテキストを比較します。|  
|[シーク](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|ステートメントまたは行の番号を指定してドキュメントのコンテキストに移動します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)