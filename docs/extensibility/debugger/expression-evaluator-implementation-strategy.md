---
title: 式エバリュエーターの実装方法 |Microsoft Docs
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
ms.openlocfilehash: a0b60a82b9451dfa43f5cd231fd38dd32b1729ed
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233049"
---
# <a name="expression-evaluator-implementation-strategy"></a>式エバリュエーターの実装方法
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細については、次を参照してください。 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター (EE) を迅速に作成する方法の 1 つは、最初にローカル変数を表示するために必要な最小限のコードを実装する、**ローカル**ウィンドウ。 理解すると便利ですのそれぞれの線、**ローカル**ウィンドウは、名前、種類、および、ローカル変数の値が表示されます。 およびによって表される 3 つすべてを[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)オブジェクト。 名前、種類、およびローカル変数の値を取得してから、`IDebugProperty2`オブジェクトを呼び出すことによってその[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッド。 ローカル変数を表示する方法について、**ローカル**ウィンドウを参照してください[表示の [ローカル]](../../extensibility/debugger/displaying-locals.md)します。  
  
## <a name="discussion"></a>説明  
 実装に考えられる実装のシーケンスを開始[IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)します。 [解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)と[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)ローカル変数を表示するメソッドを実装する必要があります。 呼び出す`IDebugExpressionEvaluator::GetMethodProperty`を返します、`IDebugProperty2`メソッドを表すオブジェクトを: これは、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)オブジェクト。 メソッド自体に表示されない、**ローカル**ウィンドウ。  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)メソッドを次に実装する必要があります。 デバッグ エンジン (DE) を渡すことによって、ローカル変数と引数の一覧を取得するには、このメソッドを呼び出して`IDebugProperty2::EnumChildren`、`guidFilter`の引数`guidFilterLocalsPlusArgs`します。 `IDebugProperty2::EnumChildren` 呼び出し[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)と[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)、1 つの列挙の結果を結合します。 参照してください[ローカル変数を表示](../../extensibility/debugger/displaying-locals.md)の詳細。  
  
## <a name="see-also"></a>関連項目  
 [式エバリュエーターを実装します。](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [ローカル変数の表示](../../extensibility/debugger/displaying-locals.md)