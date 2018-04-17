---
title: ローカルの実装のサンプル |Microsoft ドキュメント
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
ms.openlocfilehash: 56ac92989abe929884ac029e3b9c9c7dafad5fd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sample-implementation-of-locals"></a>ローカルの実装のサンプル
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 式エバリュエーター (EE) から、Visual Studio がメソッドのローカル変数を取得する方法の概要を次に示します。  
  
1.  Visual Studio は、デバッグ エンジンの (DE) を呼び出して[GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)を取得する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)をローカル変数を含む、スタック フレームのすべてのプロパティを表すオブジェクト。  
  
2.  `IDebugStackFrame2::GetDebugProperty` 呼び出し[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)を内部で、ブレークポイントが発生したメソッドを記述するオブジェクトを取得します。 デ シンボル プロバイダーを提供する ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md))、アドレス ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md))、および、バインダー ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md))。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` 呼び出し[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)指定`IDebugAddress`取得するオブジェクト、 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)指定されたアドレスを含むメソッドを表すです。  
  
4.  `IDebugContainerField`インターフェイスが照会、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)インターフェイスです。 このインターフェイス メソッドのローカル変数にアクセスできるようにすることをお勧めします。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` クラスをインスタンス化 (と呼ばれる`CFieldProperty`サンプル) を実装する、`IDebugProperty2`メソッドのローカル変数を表すインターフェイス。 `IDebugMethodField`オブジェクトは、この配置は`CFieldProperty`オブジェクトと共に、 `IDebugSymbolProvider`、`IDebugAddress`と`IDebugBinder`オブジェクト。  
  
6.  ときに、`CFieldProperty`オブジェクトが初期化されて、 [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)で呼び出されると、`IDebugMethodField`を取得するオブジェクト、 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md)メソッド自体は表示可能なすべての情報を含む構造体.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` 返します、`CFieldProperty`オブジェクトとして、`IDebugProperty2`オブジェクト。  
  
8.  Visual Studio 呼び出し[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)で返された`IDebugProperty2`フィルターを持つオブジェクト`guidFilterLocalsPlusArgs`です。 これを返します、 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)メソッドのローカル変数を含むオブジェクト。 この列挙体の呼び出しによって入力されます[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)と[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)です。  
  
9. Visual Studio 呼び出し[次](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)を取得する、 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)各ローカルの構造体。 この構造体へのポインターを含む、`IDebugProperty2`ローカルのインターフェイスです。  
  
10. Visual Studio 呼び出し[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)をローカルの名前、値、および種類を取得するには、各ローカルです。 これは、情報に表示される、**ローカル**ウィンドウです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [GetMethodProperty の実装](../../extensibility/debugger/implementing-getmethodproperty.md)  
 実装を示して[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)です。  
  
 [ローカルの列挙](../../extensibility/debugger/enumerating-locals.md)  
 デバッグ エンジン (DE) がローカル変数または引数を列挙する呼び出しを行う方法について説明します。  
  
 [ローカル プロパティの取得](../../extensibility/debugger/getting-local-properties.md)  
 名前、型、および 1 つまたは複数のローカル変数の値を取得する呼び出しを使用して、DE 方法について説明します。  
  
 [ローカル値の取得](../../extensibility/debugger/getting-local-values.md)  
 評価コンテキストによって指定されたバインダー オブジェクトのサービスを必要とすると、ローカルの値を取得するについて説明します。  
  
 [ローカル変数の評価](../../extensibility/debugger/evaluating-locals.md)  
 ローカル変数を評価する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 DE、式エバリュエーター (EE) の呼び出し時に渡される引数を提供します。  
  
 [MyCEE サンプル](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 MyC 言語の式エバリュエーターを作成するための 1 つの実装方法を示します。  
  
## <a name="see-also"></a>関連項目  
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)