---
title: IDebugIDECallback |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d05b2ab4c4944cbcce7f920f86eec0ca2f93865a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008219"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 デバッガーの出力ウィンドウにメッセージを表示する式エバリュエーター (EE) を有効にします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このコールバックは、マネージ デバッグ エンジンによって実装されます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デバッガーの出力ウィンドウに出力を送信する、式エバリュエーターで使用できます。  
  
## <a name="methods"></a>メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|デバッガーの出力ウィンドウには、指定したメッセージ文字列を送信します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Ee.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll