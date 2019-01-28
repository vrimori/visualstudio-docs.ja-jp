---
title: IDebugPortSupplier3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4cc5847d2d3403ddb1624ecd97084ad4d548ad3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030900"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
このインターフェイスは、ポート サプライヤーが (ディスクに書き込む) ことによって、デバッガーの呼び出しの間でポートを保持して、それらの保存されたポートの一覧を取得するかどうかを確認する呼び出し元を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート サプライヤーは、永続化やディスクへのポート情報の保存をサポートするには、このインターフェイスを実装します。 同じオブジェクトでこのインターフェイスを実装する必要があります、 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugPortSupplier2`をこのインターフェイスを取得するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 継承されたメソッドだけでなく、 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイスでは、このインターフェイスは、次をサポートします。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|ポート サプライヤーが、(ディスクに書き込む) ことによってポートをデバッガーの呼び出しの間で永続化できるかどうかを返します。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|このポートのサプライヤーによってディスクに書き込まれたすべてのポートを列挙するために使用できるオブジェクトを返します。|  
  
## <a name="remarks"></a>Remarks  
 ポート サプライヤーは、呼び出し間でポートを保持することができます、このインターフェイスを実装にする必要があります。 ポート サプライヤーのインスタンス化し、ポート サプライヤーが破棄されるときにディスクに書き込まれるときに、ポートを読み込む必要があります。  
  
 通常、デバッグ エンジンは、ポート サプライヤーと対話しないし、このインターフェイスの使用はありません。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)