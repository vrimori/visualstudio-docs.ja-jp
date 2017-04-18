---
title: "IDebugActivateDocumentEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 673ead5a81cf0037d794f315ac7731e2500b8fe3
ms.lasthandoff: 04/05/2017

---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
デバッグ エンジン (DE) では、このインターフェイスを使用して、読み込まれるドキュメントを要求します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デは、ソース ファイルを開く必要があるときに、このインターフェイスを実装します。 このインターフェイスは、デバッグ エンジンの操作やスクリプトに対するインタープリターの役割の一部であることによってのみ実装されます。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります (、SDM を使用して[QueryInterface](/cpp/atl/queryinterface)にアクセスする、`IDebugEvent2`インターフェイス)。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは、作成し、ソース ファイルを表示する必要があるときに、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって提供されるコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugActivateDocumentEvent2`します。  
  
|メソッド|説明|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|アクティブ化するドキュメントを取得します。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|ドキュメント内の位置を説明するドキュメントのコンテキストを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスを使用する一般的なシナリオは、解析エラーを使用してドキュメントを表示できるように、DE、スクリプトが、SDM にこのインターフェイスを送信解析エラーは、HTML ページ上のスクリプト コードで発生する場合です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
