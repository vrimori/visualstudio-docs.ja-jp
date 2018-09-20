---
title: ローカル変数の実装のサンプル |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3faf3e42442db03bbb40bbc3e726b909956d4187
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370868"
---
# <a name="sample-implementation-of-locals"></a>ローカル変数のサンプルの実装
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細については、次を参照してください。 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 Visual Studio を取得する方法、ローカル変数をメソッドの式エバリュエーター (EE) からの概要を次に示します。  
  
1.  Visual Studio はデバッグ エンジン (DE) を呼び出して[GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)を取得する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)ローカル変数のスタック フレームのすべてのプロパティを表すオブジェクト。  
  
2.  `IDebugStackFrame2::GetDebugProperty` 呼び出し[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)をブレークポイントが発生したメソッドを記述するオブジェクトを取得します。 シンボル プロバイダーを提供する、DE ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md))、アドレス ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md))、およびバインダー ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md))。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` 呼び出し[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)指定した`IDebugAddress`取得するオブジェクト、 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)指定されたアドレスを格納しているメソッドを表します。  
  
4.  `IDebugContainerField`インターフェイスが照会されます、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)インターフェイス。 このインターフェイス メソッドのローカル変数にアクセスできるようにすることをお勧めします。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` クラスをインスタンス化します (と呼ばれる`CFieldProperty`サンプル) を実行する、`IDebugProperty2`をメソッドのローカル変数を表すインターフェイス。 `IDebugMethodField`オブジェクトがこの配置`CFieldProperty`オブジェクトと共に、 `IDebugSymbolProvider`、 `IDebugAddress`、および`IDebugBinder`オブジェクト。  
  
6.  ときに、`CFieldProperty`オブジェクトが初期化される[GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)で呼び出される、`IDebugMethodField`取得するオブジェクト、 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md)メソッド自体に関する表示可能なすべての情報を含む構造体。  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` 返します、`CFieldProperty`オブジェクトとして、`IDebugProperty2`オブジェクト。  
  
8.  Visual Studio 呼び出し[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)返された`IDebugProperty2`でフィルター処理されたオブジェクト`guidFilterLocalsPlusArgs`、返された、 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)メソッドのローカル変数を含むオブジェクト。 この列挙体への呼び出しによって入力されます[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)と[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)します。  
  
9. Visual Studio 呼び出し[次](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)を取得する、 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)構造体の各ローカルです。 この構造体にはへのポインターが含まれています、`IDebugProperty2`ローカル インターフェイス。  
  
10. Visual Studio 呼び出し[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)のローカルの名前、値、および種類を取得するには、各ローカルです。 この情報が表示されます、**ローカル**ウィンドウ。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [GetMethodProperty を実装します。](../../extensibility/debugger/implementing-getmethodproperty.md)  
 実装について説明します[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)します。  
  
 [ローカル変数を列挙します。](../../extensibility/debugger/enumerating-locals.md)  
 デバッグ エンジン (DE) がローカル変数または引数を列挙するために呼び出しを実行する方法について説明します。  
  
 [ローカル プロパティを取得します](../../extensibility/debugger/getting-local-properties.md)  
 デが名、型、および 1 つまたは複数のローカル変数の値を取得する呼び出しを実行する方法について説明します。  
  
 [ローカルの値を取得します。](../../extensibility/debugger/getting-local-values.md)  
 評価コンテキストによって指定されたバインダー オブジェクトのサービスを必要とすると、ローカルの値の取得について説明します。  
  
 [ローカル変数を評価します。](../../extensibility/debugger/evaluating-locals.md)  
 ローカル変数を評価する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 DE、式エバリュエーター (EE) の呼び出し時に渡される引数を提供します。  
  
 [MyCEE サンプル](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f)  
 MyC 言語の式エバリュエーターを作成する 1 つの実装方法を示します。  
  
## <a name="see-also"></a>関連項目  
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)