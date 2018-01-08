---
title: "IEnumDebugAddresses |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses
helpviewer_keywords: IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 839d6d23e358cc3a35085d90abfa2efae11b22eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [シンボル プロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)