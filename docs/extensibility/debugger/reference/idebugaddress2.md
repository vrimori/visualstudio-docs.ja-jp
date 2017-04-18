---
title: "IDebugAddress2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 10
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
ms.openlocfilehash: e36f2863680dea79451e57d06bd749b52fbed933
ms.lasthandoff: 04/05/2017

---
# <a name="idebugaddress2"></a>IDebugAddress2
このインターフェイスは、このインターフェイスによって表されるアドレスを持つオブジェクトを所有するプロセスの ID へのアクセスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーを実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイスです。 このインターフェイスは、このアドレスに関連付けられているオブジェクトを所有するプロセスの ID へのアクセスを提供します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用して[QueryInterface](/cpp/atl/queryinterface)からこのインターフェイスを取得、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承したメソッドに加えて、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|このインターフェイスによって表されるオブジェクトを所有するプロセスの ID を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボル プロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
