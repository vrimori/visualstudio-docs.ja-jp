---
title: "評価コンテキスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9a490ef7c4ea42fe85c291ee913d7ad5e1cda1bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="evaluation-context"></a>評価コンテキスト
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 3 つの引数が渡されるデバッグ エンジン (DE) を呼び出すと、式エバリュエーター (EE)、 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)次の表に示すように検索すると、シンボルを評価するコンテキストを決定します。  
  
## <a name="arguments"></a>引数  
  
|引数|説明|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)シンボルの識別に使用するシンボル ハンドラー (SH) を指定するインターフェイスです。|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)実行の現在のポイントを指定するインターフェイスです。 実行対象のコードが含まれるメソッドを検索するために使用できます。|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)値と指定した名前のシンボルの型を検索するために使用するインターフェイスです。|  
  
 `IDebugParsedExpression::EvaluateSync`返します、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)結果の値とその型を表すインターフェイス。  
  
## <a name="see-also"></a>参照  
 [キー式エバリュエーター インターフェイス](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [ローカル変数を表示します。](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)