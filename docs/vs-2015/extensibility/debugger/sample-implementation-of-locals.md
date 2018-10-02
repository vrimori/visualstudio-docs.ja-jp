---
title: ローカル変数の実装のサンプル |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21f8e66cb597b4c70969767eefd36a7483262026
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547469"
---
# <a name="sample-implementation-of-locals"></a>ローカルの実装のサンプル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サンプルの実装のローカル](https://docs.microsoft.com/visualstudio/extensibility/debugger/sample-implementation-of-locals)します。  
  
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター (EE) から、Visual Studio がメソッドのローカル変数を取得する方法の概要を次に示します。  
  
1.  Visual Studio はデバッグ エンジン (DE) を呼び出して[GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)を取得する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)ローカル変数のスタック フレームのすべてのプロパティを表すオブジェクト。  
  
2.  `IDebugStackFrame2::GetDebugProperty` 呼び出し[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)をブレークポイントが発生したメソッドを記述するオブジェクトを取得します。 シンボル プロバイダーを提供する、DE ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md))、アドレス ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md))、およびバインダー ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md))。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` 呼び出し[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)指定`IDebugAddress`取得するオブジェクト、 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)指定されたアドレスを格納しているメソッドを表します。  
  
4.  `IDebugContainerField`インターフェイスが照会されます、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)インターフェイス。 このインターフェイス メソッドのローカル変数にアクセスできるようにすることをお勧めします。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` クラスをインスタンス化します (と呼ばれる`CFieldProperty`サンプル) を実装する、`IDebugProperty2`をメソッドのローカル変数を表すインターフェイス。 `IDebugMethodField`オブジェクトがこの配置`CFieldProperty`オブジェクトと共に、 `IDebugSymbolProvider`、`IDebugAddress`と`IDebugBinder`オブジェクト。  
  
6.  ときに、`CFieldProperty`オブジェクトが初期化される[GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)で呼び出される、`IDebugMethodField`オブジェクトを取得する、 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md)メソッド自体に関する表示可能なすべての情報を含む構造体.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` 返します、`CFieldProperty`オブジェクトとして、`IDebugProperty2`オブジェクト。  
  
8.  Visual Studio 呼び出し[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)返された`IDebugProperty2`でフィルター処理されたオブジェクト`guidFilterLocalsPlusArgs`します。 これにより返されます、 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)メソッドのローカル変数を含むオブジェクト。 この列挙体への呼び出しによって入力されます[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)と[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)します。  
  
9. Visual Studio 呼び出し[次](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)を取得する、 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)構造体の各ローカルです。 この構造体にはへのポインターが含まれています、`IDebugProperty2`ローカル インターフェイス。  
  
10. Visual Studio 呼び出し[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)のローカルの名前、値、および種類を取得するには、各ローカルです。 これに表示される情報、**ローカル**ウィンドウ。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [GetMethodProperty の実装](../../extensibility/debugger/implementing-getmethodproperty.md)  
 実装について説明します[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)します。  
  
 [ローカルの列挙](../../extensibility/debugger/enumerating-locals.md)  
 デバッグ エンジン (DE) がローカル変数または引数を列挙するために呼び出しを実行する方法について説明します。  
  
 [ローカル プロパティの取得](../../extensibility/debugger/getting-local-properties.md)  
 デが名、型、および 1 つまたは複数のローカル変数の値を取得する呼び出しを実行する方法について説明します。  
  
 [ローカル値の取得](../../extensibility/debugger/getting-local-values.md)  
 評価コンテキストによって指定されたバインダー オブジェクトのサービスを必要とすると、ローカルの値を取得するについて説明します。  
  
 [ローカル変数の評価](../../extensibility/debugger/evaluating-locals.md)  
 ローカル変数を評価する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 DE、式エバリュエーター (EE) の呼び出し時に渡される引数を提供します。  
  
 [MyCEE サンプル](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 MyC 言語の式エバリュエーターを作成する 1 つの実装方法を示します。  
  
## <a name="see-also"></a>関連項目  
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)

