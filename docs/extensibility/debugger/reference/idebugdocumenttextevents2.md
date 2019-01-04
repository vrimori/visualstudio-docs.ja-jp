---
title: IDebugDocumentTextEvents2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f0f6a1ce151ae78032d862926f55cc55e650624
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895598"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
このインターフェイスは、Visual Studio によってデバッグ エンジンによって提供されるソース ドキュメントへの変更通知に使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、ソース コードに変更をサポートするためにこのインターフェイスを実装します。 このインターフェイスが実装する同一のオブジェクトに通常実装、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 呼び出すことによってこのインターフェイスを取得、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>メソッド。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>インターフェイスがへの呼び出しから取得した、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>メソッド。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスを呼び出すことによって取得、 [QueryInterface](/cpp/atl/queryinterface)メソッドを[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugDocumentTextEvents2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|ドキュメント全体が破棄されたことを示します。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|デバッグ パッケージをドキュメントにテキストが挿入されたことを通知します。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|テキストがドキュメントから削除されているパッケージのデバッグに通知します。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|デバッグ パッケージ、ドキュメント内のテキストが置き換えられることを通知します。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|テキスト属性をドキュメントで更新されていることをデバッグ パッケージに通知します。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|ドキュメントの属性が更新されているイベントの受信側に通知します。|  
  
## <a name="remarks"></a>Remarks  
 だけで、各自のドキュメントを提供するデバッグ エンジンを活用、`IDebugDocumentTextEvent2`インターフェイス。 この例は、スクリプトのデバッグ エンジンになります。 スクリプトを解釈するには、プロセスで新しいソース コードを生成できますが、ディスク ファイルに存在しないと、DE のみが知っているを。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)