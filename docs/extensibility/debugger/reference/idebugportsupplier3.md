---
title: IDebugPortSupplier3 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5a35e212c98d6e62b667c4305d8ae4874feb3aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116998"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
このインターフェイスは、ポート サプライヤーことができます (それらをディスクに書き込む) によって、デバッガーの呼び出しの間でポートを保持してし、それらの保存されたポートの一覧を取得するかどうかを確認する呼び出し元を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート仕入先では、永続化やポート情報をディスクに保存をサポートするには、このインターフェイスを実装します。 同じオブジェクトでこのインターフェイスを実装する必要があります、 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugPortSupplier2`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承したメソッドに加えて、 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイス、このインターフェイスは、次をサポートしています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|ポート サプライヤーが、(それらをディスクに書き込む) をポートをデバッガーの呼び出しの間で永続化できるかどうかを返します。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|このポート業者によってディスクに書き込まれたすべてのポートを介して列挙に使用できるオブジェクトを返します。|  
  
## <a name="remarks"></a>コメント  
 ポート サプライヤーは、呼び出し間でポートを保持することができます、このインターフェイスを実装してする必要があります。 ポートは、ポート サプライヤーがインスタンス化、およびポート供給業者が破棄されるときにディスクに書き込まれます時に読み込まれる必要があります。  
  
 通常、デバッグ エンジンは、ポート サプライヤーとは対話しませんし、このインターフェイスの使用はありません。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)