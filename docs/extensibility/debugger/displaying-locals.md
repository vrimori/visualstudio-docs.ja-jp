---
title: ローカルの表示 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: e4fbc85b9b45b668d4c183d5b5068fc190f0a2f6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852600"
---
# <a name="display-locals"></a>ローカル変数の表示
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細については、次を参照してください。 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 常に実行では、それを含むメソッドとも呼ばれるメソッドまたは現在のメソッドのコンテキスト内で行われます。 実行が一時停止したときに、Visual Studio は、デバッグ エンジンのローカル変数の一覧を取得するには、(DE) と総称メソッドのローカル変数の引数を呼び出します。 Visual Studio は、これらのローカル変数とその値が表示されます、**ローカル**ウィンドウ。  
  
 デを呼び出すローカル変数を表示する、 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) EE に属するメソッドは、評価コンテキスト、シンボル プロバイダー (SP)、現在の実行のアドレスおよびバインダー オブジェクトを割り当てます。 詳細については、次を参照してください。[評価コンテキスト](../../extensibility/debugger/evaluation-context.md)します。 呼び出しが成功した場合、`IDebugExpressionEvaluator::GetMethodProperty`メソッドを返します。、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)オブジェクトで、現在の実行のアドレスを含むメソッドを表します。  
  
 DE 呼び出し[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)を取得する、 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)オブジェクトを唯一のローカル変数を返すフィルター処理されの一覧を生成するために列挙される[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)構造体。 各構造体には、名前、種類、およびローカルの値が含まれています。 型と値は、表示に適した、書式設定された文字列として格納されます。 名前、型、および値は通常一緒に表示の 1 つの行で、**ローカル**ウィンドウ。  
  
> [!NOTE]
>  **[クイック ウォッチ]** と**ウォッチ**windows も同じ形式で表示名、値、および型の変数を表示します。 ただし、これらの値が呼び出すことによって取得[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)の代わりに`IDebugProperty2::EnumChildren`します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ローカル変数のサンプルの実装](../../extensibility/debugger/sample-implementation-of-locals.md)  
 ローカル変数を実装するプロセスの手順を例を使用します。  
  
## <a name="related-sections"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デバッグ エンジン (DE)、式エバリュエーター (EE) を呼び出す場合に合格する 3 つの引数について説明します。  
  
## <a name="see-also"></a>関連項目  
 [CLR の式エバリュエーターを書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)