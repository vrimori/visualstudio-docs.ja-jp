---
title: IDebugApplication::SynchronousCallInDebuggerThread |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7b66b0b085c0fe3abbee3c3b8c5c3f7d252d3b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725672"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
呼び出し元がデバッガー スレッドでコードを実行するメカニズムを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pptc`  
 [in]呼び出すオブジェクト。  
  
 `dwParam1`  
 [in]最初のパラメーターに渡す、`IDebugThreadCall::ThreadCallHandler`メソッドです。  
  
 `dwParam2`  
 [in]2 番目のパラメーターに渡す、`IDebugThreadCall::ThreadCallHandler`メソッドです。  
  
 `dwParam3`  
 [in]3 番目のパラメーターに渡す、`IDebugThreadCall::ThreadCallHandler`メソッドです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 言語エンジンとホストは通常、1 つのスレッドの実装の上にフリー スレッド オブジェクトを実装するのにこのメソッドを使用します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall インターフェイス](../../winscript/reference/idebugthreadcall-interface.md)