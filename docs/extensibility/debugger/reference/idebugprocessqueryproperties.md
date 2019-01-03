---
title: IDebugProcessQueryProperties |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b74b410e64cd6f57b828947d829461bc9d490776
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905492"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
このインターフェイスによって実装される拡張機能インターフェイスは、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)実装します。 これにより、デバッグ プロセス環境に関する情報を取得する実装者ができます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ プロセスの実行環境に関する情報を取得するには、このインターフェイスを実装します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcessQueryProperties`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|プロパティ値を照会します。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|プロパティの値を照会します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスが実装されていることはほとんどありません。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Portpriv.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)