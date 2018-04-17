---
title: ローカル変数を表示する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03a3f08498e8b046b02defd32083677b7f39e7e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="displaying-locals"></a>ローカル変数を表示します。
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 常に実行では、メソッド、メソッドを含むとも呼ばれるまたは現在のメソッドのコンテキスト内で行われます。 実行は一時停止、Visual Studio はデバッグ エンジンのローカル変数の一覧を取得するには、(DE) と総称して、メソッドのローカル変数、引数を呼び出します。 Visual Studio は、これらのローカル変数とその値が表示されます、**ローカル**ウィンドウです。  
  
 デを呼び出して表示するには [ローカル]、 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) EE に属するメソッドとは、評価コンテキスト、シンボル プロバイダー (SP)、現在の実行のアドレス、およびバインダー オブジェクト。 詳細については、次を参照してください。[評価コンテキスト](../../extensibility/debugger/evaluation-context.md)です。 呼び出しが成功した場合、`IDebugExpressionEvaluator::GetMethodProperty`メソッドを返します、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)を現在の実行のアドレスが含まれるメソッドを表すオブジェクト。  
  
 DE 呼び出し[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)を取得する、 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)オブジェクトでは、フィルター選択を唯一のローカル変数を取得および列挙の一覧を生成するためには、 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)構造体。 各構造体には、名前、型、およびローカルの値が含まれています。 型および値は、表示に適切な形式の文字列として格納されます。 名前、型、および値が通常表示まとめての 1 つの行で、**ローカル**ウィンドウです。  
  
> [!NOTE]
>  **[クイック ウォッチ]**と**ウォッチ**ウィンドウも、同じ形式の名前、値、および種類を持つ変数を表示します。 ただし、これらの値が呼び出すことによって取得[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)の代わりに`IDebugProperty2::EnumChildren`です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ローカルの実装のサンプル](../../extensibility/debugger/sample-implementation-of-locals.md)  
 ローカル変数を実装するプロセスの手順を例を使用します。  
  
## <a name="related-sections"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デバッグ エンジン (DE) を呼び出すと、式エバリュエーター (EE)、それに合格する 3 つの引数について説明します。  
  
## <a name="see-also"></a>関連項目  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)