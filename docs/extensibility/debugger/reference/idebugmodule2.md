---
title: IDebugModule2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ea20dac16cdffbac24cbca68c1a337a250ea8cc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922770"
---
# <a name="idebugmodule2"></a>IDebugModule2
このインターフェイスは、モジュールを表します: プログラムの実行可能ファイル、単位は、-、DLL など。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、モジュールを表すと、そのモジュールに関する情報へのアクセスを提供するこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)このインターフェイスを返します。 DE 送信、 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)インターフェイスを使用してセッション デバッグ マネージャー (SDM)、[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)メソッド。  
  
 このインターフェイスで返される可能性も、 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造 (への呼び出しによって返される[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md))。  
  
 [[次へ]](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)もこのインターフェイスを返します ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)を返します、 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)インターフェイス)。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugModule2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|取得、 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)このモジュールを記述します。|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|互換性のために残されています。 使用しないでください。 このモジュールのシンボルを再読み込みします。|  
  
## <a name="remarks"></a>Remarks  
 モジュールの情報を表示できる、**モジュール**IDE のウィンドウ。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)