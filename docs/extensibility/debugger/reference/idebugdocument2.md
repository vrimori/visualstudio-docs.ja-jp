---
title: IDebugDocument2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36ac127e6cd6e25fd42c4859e723c883ecaffa82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocument2"></a>IDebugDocument2
このインターフェイスは、ソース ドキュメントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 通常このインターフェイスを実装します。 デバッグ エンジン (DE) は、ソース コードを指定する必要があるあり、ソースがディスクに存在しない場合、このインターフェイスを実装します。  このような場合、DE も実装[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)と[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)でいくつか追加のメソッドと同様に、インターフェイス、 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)と[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 メソッドを`IDebugDocumentContext2`、 `IDebugDisassemblyStream2`、 `IDebugDocumentPosition2`、および`IDebugActivateDocumentEvent2`インターフェイスは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDocument2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[getName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|いくつかの形式のいずれかで、ドキュメントの名前を取得します。|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|ドキュメントのクラス識別子を取得します。|  
  
## <a name="remarks"></a>コメント  
 デがソース コードを指定した場合にのみ、このインターフェイスを実装します。 たとえば、HTML ページ上のスクリプトをデバッグするとき、DE 提供ソース コード、ソースをダウンロードまたは動的に生成されるため、ディスク ファイルとして存在しません。 C++ などの従来の言語をデバッグするときにこのインターフェイスが実装する必要はありません。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)