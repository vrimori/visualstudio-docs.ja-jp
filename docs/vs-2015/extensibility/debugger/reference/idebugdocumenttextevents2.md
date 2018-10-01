---
title: IDebugDocumentTextEvents2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95eae8da7779a23e9bf285eff2f637fbcd4633e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539900"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugDocumentTextEvents2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumenttextevents2)します。  
  
このインターフェイスは、Visual Studio によってデバッグ エンジンによって提供されるソース ドキュメントへの変更通知に使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デでは、ソース コードに変更をサポートするためにこのインターフェイスを実装します。 このインターフェイスが実装する同一のオブジェクトに通常実装、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 呼び出すことによってこのインターフェイスを取得、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>メソッド。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>インターフェイスがへの呼び出しから取得した、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>メソッド。 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスを呼び出すことによって取得、 [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)メソッドを[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイス。  
  
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

