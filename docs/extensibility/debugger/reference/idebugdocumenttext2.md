---
title: "IDebugDocumentText2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2
helpviewer_keywords: IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c3540dc77821e6aa3fb3884d82cd0c83eee8e24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
このインターフェイスは、テキスト ドキュメントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、テキスト形式では、ソース コードを指定する必要があるときに、このインターフェイスを実装します。 デを実装する場合は、最も一般的なケースのため、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイスが実装する必要も、`IDebugDocumentText2`インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用して、`QueryInterface`からこのインターフェイスを取得するメソッド、`IDebugDocument2`インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、`IDebugDocument2`インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|ドキュメントのこの位置でテキストのサイズを取得します。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|ドキュメント内の指定位置からテキストを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスを実装するオブジェクトを実装する必要がありますも、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイス、ランダウン、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>のためのインターフェイス、 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)オブジェクト。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)