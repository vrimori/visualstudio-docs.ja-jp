---
title: "ローカル変数の実装のサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] ローカル変数のデバッグ"
  - "式の評価、ローカル変数"
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# ローカル変数の実装のサンプル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター \(EE\) から、Visual Studio がメソッドのローカル変数を取得する方法の概要を次に示します。  
  
1.  Visual Studio はデバッグ エンジン \(DE\) を呼び出して [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) を取得する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) をローカル変数を含むスタック フレームのすべてのプロパティを表すオブジェクト。  
  
2.  `IDebugStackFrame2::GetDebugProperty` 呼び出し [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) ブレークポイントが発生する方法について説明するオブジェクトを取得します。 シンボル プロバイダーを提供する、DE \([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)\)、アドレス \([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)\)、およびバインダー \([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\)。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` 呼び出し [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) 指定 `IDebugAddress` 取得するオブジェクト、 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 指定したアドレスを含むメソッドを表します。  
  
4.  `IDebugContainerField` インターフェイスが照会された、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) インターフェイスです。 このインターフェイス メソッドのローカル変数にアクセスできるようにすることをお勧めします。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` クラスをインスタンス化 \(と呼ばれる `CFieldProperty` のサンプル\) を実装する、 `IDebugProperty2` メソッドのローカル変数を表すインターフェイスです。`IDebugMethodField` オブジェクトがこれに配置されます `CFieldProperty` オブジェクトと共に、 `IDebugSymbolProvider`, 、`IDebugAddress` と `IDebugBinder` オブジェクトです。  
  
6.  ときに、 `CFieldProperty` オブジェクトを初期化すると、 [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) で呼び出される、 `IDebugMethodField` を取得するオブジェクト、 [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) メソッド自体は表示可能なすべての情報を含む構造体。  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` 返します、 `CFieldProperty` オブジェクトとして、 `IDebugProperty2` オブジェクトです。  
  
8.  Visual Studio 呼び出し [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) で返された `IDebugProperty2` 、フィルターを使用してオブジェクト `guidFilterLocalsPlusArgs`します。 返されます。、 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) メソッドのローカル変数を含むオブジェクト。 この列挙体がへの呼び出しによってデータ格納 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) と [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)です。  
  
9. Visual Studio 呼び出し [次へ](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) させることが、 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 各ローカルの構造です。 この構造体へのポインターを含む、 `IDebugProperty2` ローカル インターフェイスです。  
  
10. Visual Studio 呼び出し [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) でローカルの名前、値、および種類を取得するには、各ローカルです。 これに表示される情報、 **ローカル** ウィンドウです。  
  
## このセクションの内容  
 [GetMethodProperty を実装します。](../../extensibility/debugger/implementing-getmethodproperty.md)  
 実装について説明 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)します。  
  
 [\[ローカル\] の列挙](../Topic/Enumerating%20Locals.md)  
 デバッグ エンジン \(DE\) がローカル変数または引数を列挙する呼び出しを行う方法について説明します。  
  
 [ローカル プロパティの取得](../../extensibility/debugger/getting-local-properties.md)  
 名前、種類、および 1 つまたは複数のローカル変数の値を取得する呼び出しのデのしくみについて説明します。  
  
 [ローカル値を取得します。](../../extensibility/debugger/getting-local-values.md)  
 評価コンテキストによって指定されたバインダー オブジェクトのサービスを必要とすると、ローカル変数の値を取得するについて説明します。  
  
 [ローカル変数を評価します。](../../extensibility/debugger/evaluating-locals.md)  
 \[ローカル\] の評価方法について説明します。  
  
## 関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デは式エバリュエーター \(EE\) を呼び出すときに渡される引数を提供します。  
  
 [MyCEE Sample](http://msdn.microsoft.com/ja-jp/624a018b-9179-402f-9d48-3aec87b48f4f)  
 MyC 言語の式エバリュエーターを作成するための 1 つの実装方法について説明します。  
  
## 参照  
 [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)