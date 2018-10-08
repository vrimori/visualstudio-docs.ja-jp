---
title: IDebugDocumentText2 |Microsoft Docs
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
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7856512e4dc8b5bb7dfe82c82ce51af23d3959a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537787"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugDocumentText2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumenttext2)します。  
  
このインターフェイスは、テキスト ドキュメントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、指定する必要があるソース コードがテキスト形式の場合、このインターフェイスを実装します。 以降、DE が実装されている場合は、最も一般的なケースで、これは、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイスが実装する必要も、`IDebugDocumentText2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用して、`QueryInterface`からこのインターフェイスを取得するメソッド、`IDebugDocument2`インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、`IDebugDocument2`インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|ドキュメントのこの位置でテキストのサイズを取得します。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|ドキュメント内の指定した位置からテキストを取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスを実装するオブジェクトを実装する必要がありますも、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスを提供する、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>のためのインターフェイス、 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)オブジェクト。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

