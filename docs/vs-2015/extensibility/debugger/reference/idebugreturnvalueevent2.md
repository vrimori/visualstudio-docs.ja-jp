---
title: IDebugReturnValueEvent2 |Microsoft Docs
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
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd9115b68e389b5eac1ea114aed476d1f4e2c519
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288003"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、または関数をステップ実行した後、デバッグ エンジン (DE) によって、セッション デバッグ マネージャー (SDM) に送信されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デはまたはの上にステップ インが関数からの戻り値を報告するには、このインターフェイスを実装します。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このインターフェイスと同じオブジェクトでインターフェイスを実装する必要があります。 SDM を使用して[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)にアクセスする、`IDebugEvent2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デは作成し、関数の戻り値を報告するには、このイベント オブジェクトを送信します。 使用して、イベントが送信される、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ中のプログラムにアタッチされているときに、SDM によって指定されたコールバック関数。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugReturnValueEvent2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|ステップ アウトでも、関数で返される値を取得します。|  
  
## <a name="remarks"></a>Remarks  
 呼び出すことによって、関数によって返される値を取得できます[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)します。 返される値に表示されます、 **[自動変数]** ウィンドウ。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)

