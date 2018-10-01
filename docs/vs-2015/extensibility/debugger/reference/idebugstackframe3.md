---
title: IDebugStackFrame3 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f032ac6b5fb348916c51f8cc98e1726b0795e21
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534996"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugStackFrame3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe3)します。  
  
このインターフェイスは拡張[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)傍受した例外を処理します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) を実装する同一のオブジェクトにこのインターフェイスを実装する、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)傍受した例外をサポートするインターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上、`IDebugStackFrame2`をこのインターフェイスを取得するインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)、`IDebugStackFrame3`次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|任意の通常の例外処理の前に、現在のスタック フレームの例外を処理します。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|スタック アンワインドが発生した場合は、コードのコンテキストを返します。|  
  
## <a name="remarks"></a>Remarks  
 傍受した例外は、通常の例外処理ルーチンは、ランタイムによって呼び出される前に、デバッガーが例外を処理できることを意味します。 基本的に、例外をインターセプトは、例外ハンドラーがない場合にも存在が見かけ上の実行時のようになります。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)すべて通常の例外コールバック イベント中に呼び出されます (唯一の例外は、デバッグするかどうか (マネージし、アンマネージ コード)、混在モードのコード中に例外をインターセプトできない場合、最終のコールバックの場合)。 デが実装していない場合`IDebugStackFrame3`、または、DE IDebugStackFrame3 からエラーが返されます::`InterceptCurrentException` (など`E_NOTIMPL`)、デバッガーが通常、例外を処理し、します。  
  
 例外をインターセプトすることで、デバッガーはデバッグ中のプログラムの状態に変更を加えるし、例外がスローされた時点での実行を再開するユーザーを許可できます。  
  
> [!NOTE]
>  インターセプトの例外は、共通言語ランタイム (CLR) 下で実行しているプログラムでは、マネージ コードでのみ許可されます。  
  
 デバッグ エンジンを示します"metricExceptions"を設定して例外をインターセプトをサポートしている値の 1 に実行時に使用して、`SetMetric`関数。 詳細については、次を参照してください。[デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

