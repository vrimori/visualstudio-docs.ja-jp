---
title: IEnumDebugAddresses |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfed705253a03ec550e7533f7e2ab323b7ead62a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120937"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
このインターフェイスを実装するオブジェクトのコレクションを表します、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、シンボル プロバイダーを実装するオブジェクトのセットを指定する、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイスです。 存在するための標準の COM 列挙ではないことに注意してください、 [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)メソッドです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、によって返される[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)と[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|次のセットを取得[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)列挙体からのオブジェクト。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|指定されたエントリ数をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|最初のエントリを列挙型をリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|現在の列挙型のコピーを取得します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|列挙体のエントリの数を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、式エバリュエーターに指定する適切なアドレスを特定するため、デバッグ エンジンで通常使用されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボル プロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)