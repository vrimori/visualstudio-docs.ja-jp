---
title: 式エバリュエーターの実装方法 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 757e74a9dde1c580a6116342948edd4eb42f9ca3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737895"
---
# <a name="expression-evaluator-implementation-strategy"></a>式エバリュエーターの実装方法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター (EE) を迅速に作成する方法の 1 つは、最初にローカル変数を表示するために必要な最小限のコードを実装する、**ローカル**ウィンドウ。 理解すると便利ですのそれぞれの線、**ローカル**ウィンドウは、名前、種類、および、ローカル変数の値が表示されます。 およびによって表される 3 つすべてを[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)オブジェクト。 名前、種類、およびローカル変数の値から取得できます、`IDebugProperty2`オブジェクトを呼び出すことによってその[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッド。 ローカル変数を表示する方法について、**ローカル**ウィンドウを参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)します。  
  
## <a name="discussion"></a>説明  
 実装に考えられる実装のシーケンスを開始[IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)します。 [解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)と[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)メソッドを実装して、ローカル変数を表示する必要があります。 呼び出す`IDebugExpressionEvaluator::GetMethodProperty`を返します、`IDebugProperty2`メソッドを表すオブジェクトを: これは、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)オブジェクト。 メソッド自体に表示されない、**ローカル**ウィンドウ。  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)メソッドを次に実装する必要があります。 デバッグ エンジン (DE) を渡すことによって、ローカル変数と引数の一覧を取得するには、このメソッドを呼び出して`IDebugProperty2::EnumChildren`、`guidFilter`の引数`guidFilterLocalsPlusArgs`します。 `IDebugProperty2::EnumChildren` 呼び出し[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)と[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)、1 つの列挙の結果を結合します。 参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)の詳細。  
  
## <a name="see-also"></a>関連項目  
 [式エバリュエーターの実装](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)

