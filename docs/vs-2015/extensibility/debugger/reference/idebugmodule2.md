---
title: IDebugModule2 |Microsoft Docs
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
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 941dee1c8cf9bdf3aaa4fe2f69ff7da95eac0f87
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237212"
---
# <a name="idebugmodule2"></a>IDebugModule2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

