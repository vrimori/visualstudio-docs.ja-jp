---
title: "IDebugPortSupplier3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
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
ms.openlocfilehash: 0eb7cf542fa61d53220cd10f54e3fbd7c6165bf4
ms.lasthandoff: 04/05/2017

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
