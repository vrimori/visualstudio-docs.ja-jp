---
title: IDebugDocument2 |Microsoft Docs
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
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 59f698ca67cbc144bbd7f3874a85beae45ddfbb5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194039"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、ソース ドキュメントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 一般にこのインターフェイスを実装します。 デバッグ エンジン (DE) は、ソース コードを指定する必要があるあり、ソースがディスクに存在しない場合にも、このインターフェイスに実装できます。  このような場合、DE は実装にも[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)と[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)で追加のメソッドと同様に、インターフェイス、 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)と[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 上のメソッド、 `IDebugDocumentContext2`、 `IDebugDisassemblyStream2`、 `IDebugDocumentPosition2`、および`IDebugActivateDocumentEvent2`インターフェイスは、このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDocument2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|いくつかの形式のいずれかで、ドキュメントの名前を取得します。|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|ドキュメントのクラス識別子を取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、DE、ソース コードを提供する場合にのみ実装されます。 たとえば、HTML ページ上のスクリプトをデバッグする場合、DE を提供ソース コード、ソースをダウンロードまたは動的に生成されるため、ディスク ファイルとして存在しません。 C++ などの従来の言語をデバッグするときに、このインターフェイスを実装する必要はありません。  
  
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

