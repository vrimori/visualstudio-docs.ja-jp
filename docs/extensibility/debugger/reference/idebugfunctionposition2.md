---
title: IDebugFunctionPosition2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61fd298b1bbbf28f7a7fe514a01dc5707c35e04b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840935"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
このインターフェイスは、関数のソース ドキュメント内の抽象の位置を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、ソース ドキュメント内の関数の位置を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスがの一部として提供される、 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)共用体 (具体的を[BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)構造) の一部で、さらに、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)この構造を使用して、保留中のブレークポイントの作成に使用します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugFunctionPosition2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|この位置が関連している関数の名前を取得します。|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|関数の先頭からのオフセットを取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスによって表される位置がテキスト ベース、具体的を[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)構造体。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)