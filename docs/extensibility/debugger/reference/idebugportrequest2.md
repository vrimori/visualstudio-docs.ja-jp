---
title: "IDebugPortRequest2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5b47a9bde47049c957af9f60e1d09d03b55c2359
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
このインターフェイスでは、ポートについて説明します。 この説明を使用すると、ポートのサプライヤーにポートを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio は、通常、ポート業者からのデバッグ ポートの取得中には、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスに渡される[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)デバッグ ポートを作成します。 呼び出し[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)このインターフェイスは、最初の場所、ポートの作成に使用される、要求を表すを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPortRequest2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|作成するポートの名前を取得します。|  
  
## <a name="remarks"></a>コメント  
 通常、デバッグ エンジンは、ポート サプライヤーとは対話しませんし、このインターフェイスの使用はありません。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)