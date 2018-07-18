---
title: IDebugExpressionEvaluator3 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2349924dd2f762638dc6ea08b40a71776b9605a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122770"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 強化されたパーサー ツリー式エバリュエーター (EE) を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このバージョンのパーサーは、シンボルのプロバイダーおよび評価するフレームのアドレスを渡します。  
  
## <a name="methods"></a>メソッド  
 メソッドだけでなく、 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)インターフェイス、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|式の文字列をシンボル プロバイダーおよび評価するフレームのアドレス指定解析された式に変換します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll