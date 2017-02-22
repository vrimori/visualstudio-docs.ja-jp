---
title: "[ローカル] を表示します。 | Microsoft Docs"
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
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式の評価、ローカル変数を表示します。"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# [ローカル] を表示します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 含むメソッドとも呼ばれるメソッドまたは現在のメソッドのコンテキスト内で常に実行が行われます。 実行が一時停止、Visual Studio はデバッグ エンジンのローカル変数の一覧を取得するには、\(DE\) と総称メソッドのローカル変数、引数を呼び出します。 Visual Studio は、これらのローカル変数とその値を表示、 **ローカル** ウィンドウです。  
  
 デを呼び出すローカル変数を表示する、 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) EE に属するメソッドにし、評価コンテキスト、シンボル プロバイダー \(SP\)、現在の実行のアドレスおよびバインダー オブジェクトを移します。 詳細については、「[評価コンテキスト](../../extensibility/debugger/evaluation-context.md)」を参照してください。 呼び出しが成功した場合、 `IDebugExpressionEvaluator::GetMethodProperty` メソッドを返します。、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) を現在の実行のアドレスを含むメソッドを表すオブジェクト。  
  
 DE 呼び出し [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) を取得する、 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) を唯一のローカル変数を返すフィルター処理され、列挙の一覧を生成するオブジェクト [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 構造体。 各構造体には、名前、種類、およびローカルの値が含まれています。 型および値は、表示に適した書式付きの文字列として格納されます。 名前、型、および値は通常一緒に表示の 1 つの行で、 **ローカル** ウィンドウです。  
  
> [!NOTE]
>  **\[クイック ウォッチ\]** と **ウォッチ** windows も同じ形式で表示名、値、および型の変数を表示します。 ただし、それらの値が呼び出すことによって取得 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) の代わりに `IDebugProperty2::EnumChildren`します。  
  
## このセクションの内容  
 [ローカル変数の実装のサンプル](../../extensibility/debugger/sample-implementation-of-locals.md)  
 例を使用して、順をおってのローカル変数を実装します。  
  
## 関連項目  
 [評価コンテキスト](../../extensibility/debugger/evaluation-context.md)  
 デバッグ エンジン \(DE\) は、式エバリュエーター \(EE\)、呼び出すときは、3 つの引数合格したことについて説明します。  
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)