---
title: IDebugProcessSecurity |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e34a93e73bd1c4c9b5e70f89d318c2db6a84f2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967957"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` 安全なプロセスにアタッチがユーザーに警告するポートのサプライヤーによって実装されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcessSecurity`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|ポート サプライヤーからユーザー名を取得します。|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|ユーザーに警告する、デバッグ プロセスにアタッチする安全ではありません。|  
  
## <a name="remarks"></a>Remarks  
 警告が表示し、ユーザーが接続しているプロセスは、安全でない考慮できる場合はキャンセルできるようにするには、このインターフェイスを実装します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [ポート](../../../extensibility/debugger/ports.md)   
 [ポート サプライヤー](../../../extensibility/debugger/port-suppliers.md)   
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)