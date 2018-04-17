---
title: IDebugDocumentPositionOffset2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f08b278d75068351d6d65511f74209c7208024cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
ソース ファイル内の文字オフセットとしての位置を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 IDE によって実装され、デバッグ エンジンで使用します。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugDocumentPositionOffset2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|現在のドキュメントの位置の範囲を取得します。|  
  
## <a name="remarks"></a>コメント  
 同じ情報が返されます。 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)が`char`ドキュメントの先頭から数分オフセットします。 これにより、その上に存在します、ディスク、つまり、通常返される行と列の情報ではなく、文字の 1 次元の配列と同じように、ドキュメントが表示されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)