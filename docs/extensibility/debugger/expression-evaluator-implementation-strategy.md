---
title: 式エバリュエーターの実装方法 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67b2496c2e30428cd4cc830526e53cf0cc61fdd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102435"
---
# <a name="expression-evaluator-implementation-strategy"></a>式エバリュエーターの実装方法
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 式エバリュエーター (EE) を迅速に作成する方法の 1 つは、最初にローカル変数を表示するために必要な最小限のコードを実装する、**ローカル**ウィンドウです。 理解すると便利なのそれぞれの線、 **[ローカル]** ウィンドウは、名前、型、およびローカル変数の値が表示されます。 およびによって表される 3 つのすべて、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)オブジェクト。 名前、型、およびローカル変数の値から取得できます、`IDebugProperty2`オブジェクトを呼び出してその[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッドです。 ローカル変数を表示する方法について、 **[ローカル]** ウィンドウを参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)です。  
  
## <a name="discussion"></a>説明  
 可能な実装順序を実装するための開始[IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)です。 [解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)と[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)メソッドは、ローカル変数を表示するために実装する必要があります。 呼び出す`IDebugExpressionEvaluator::GetMethodProperty`を返します、`IDebugProperty2`メソッドを表すオブジェクト。 つまり、、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)オブジェクト。 メソッド自体に表示されない、**ローカル**ウィンドウです。  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)メソッドを次に実装する必要があります。 デバッグ エンジン (DE) を渡すことによってローカル変数と引数の一覧を取得するには、このメソッドを呼び出します`IDebugProperty2::EnumChildren`、`guidFilter`の引数`guidFilterLocalsPlusArgs`です。 `IDebugProperty2::EnumChildren` 呼び出し[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)と[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)、1 つの列挙の結果を結合します。 参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)詳細についてはします。  
  
## <a name="see-also"></a>関連項目  
 [式エバリュエーターを実装します。](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)