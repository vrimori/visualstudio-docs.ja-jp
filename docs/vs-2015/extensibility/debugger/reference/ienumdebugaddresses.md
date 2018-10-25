---
title: IEnumDebugAddresses |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84216b91506169a221dbee44d17fd686922e4feb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292930"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスを実装するオブジェクトのコレクションを表します、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイス。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスを実装するオブジェクトのセットを指定するシンボル プロバイダーによって実装されます、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイス。 存在するための標準 COM 列挙型ではないことに注意してください、 [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)メソッド。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、によって返される[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)と[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|次のセットを取得します。 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)列挙体からのオブジェクト。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|指定されたエントリ数をスキップします。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|最初のエントリを列挙型をリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|現在の列挙体のコピーを取得します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|列挙内のエントリの数を取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、式エバリュエーターにできるようにする適切なアドレスを確認するためのデバッグ エンジンで通常使用されます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)

