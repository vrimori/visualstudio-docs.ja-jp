---
title: "IDebugModule2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa4044e6490f8de8228541787b7bf8ab80285a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
このインターフェイスは、モジュールを表す-プログラムの実行可能ファイル、単位は、— DLL などです。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、モジュールを表すそのモジュールに関する情報へのアクセスを提供して、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)このインターフェイスを返します。 DE 送信、 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)インターフェイスを使用して、セッション デバッグ マネージャー (SDM) を[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)メソッドです。  
  
 このインターフェイスはでも返される、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造 (への呼び出しによって返される[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md))。  
  
 [[次へ]](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)もこのインターフェイスを返します ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)を返します、 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)インターフェイス)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugModule2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|取得、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)このモジュールを記述します。|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|互換性のために残されています。 使用しないでください。 このモジュールのシンボルを再読み込みします。|  
  
## <a name="remarks"></a>コメント  
 モジュールの情報に表示できる、**モジュール**IDE のウィンドウ。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)