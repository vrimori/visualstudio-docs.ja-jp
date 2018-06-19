---
title: IDebugProgramNodeAttach2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a83f5635dfacb638a2e76054dc5ed4e887e2a3cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120690"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
プログラム ノードが関連付けられているプログラムにアタッチしようとする通知を許可します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、同じを実装するクラスの実装、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)アタッチ操作の通知を受信するために、アタッチ操作をキャンセルする機会を提供するインターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを呼び出すことによって取得、`QueryInterface`メソッドで、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)オブジェクト。 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)する前にメソッドを呼び出す必要があります、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドを [プログラム] ノード、attach プロセスを停止する機会を提供します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスでは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|関連付けられているプログラムにアタッチするか、attach プロセスには、ゆだねます、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドです。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、非推奨に代わる[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)メソッドです。 すべてのデバッグ エンジンが読み込まれて常に、`CoCreateInstance`関数では、デバッグ中のプログラムのアドレス空間の外部オブジェクトのインスタンスは、します。  
  
 場合の以前の実装、`IDebugProgramNode2::Attach_V7`メソッドは単に設定された、`GUID`のデバッグ中のプログラムをのみ、 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)メソッドを実装する必要があります。  
  
 以前の実装の場合、`IDebugProgramNode2::Attach_V7`メソッドは、指定されたコールバック インターフェイスを使用し、その機能の実装に移動する必要があります、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドおよび`IDebugProgramNodeAttach2`インターフェイスでは不要実装する必要です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)