---
title: "IDebugBeforeSymbolSearchEvent2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9541c7008129f47df93e2e4cf2c3e8248742b0c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
デバッグ エンジン (DE) は、シンボルの読み込み中にバーのメッセージをセッション デバッグ マネージャーの状態を設定するには、(SDM) のこのインターフェイスを送信します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 これには、シンボルの読み込み中に、ステータス バー メッセージを設定する必要があります、デはこのインターフェイスを実装します。 このインターフェイスは、デバッグ エンジンの操作やスクリプトに対するインタープリターの役割の一部であることによってのみ実装されます。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトのインターフェイスを実装する必要があります (、SDM を使用して**QueryInterface**にアクセスする、 **IDebugEvent2**インターフェイス)。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは、作成し、これには、シンボルの読み込み中に、ステータス バー メッセージを設定する必要があります、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムに添付するときに、SDM によって提供されるコールバック関数。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugBeforeSymbolSearchEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|現在デバッグ中のモジュールの名前を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll