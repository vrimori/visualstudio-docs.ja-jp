---
title: IDebugPortSupplierEx2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbc58f85a084711057e2ad46b03a1ac0f6fb8f28
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866779"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
選択し、コア サーバーと通信のポート サプライヤーのサポートを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 使用するコア サーバーを選択できるように、カスタム ポート サプライヤーはこのインターフェイスを実装します。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの**IDebugPortSupplierEx2**します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|ポート サプライヤーのコア サーバーを設定します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Portpriv.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)