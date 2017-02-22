---
title: "ローカルの値を変更します。 | Microsoft Docs"
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
  - "式の評価、プログラムで値を変更します。"
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# ローカルの値を変更します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 \[値\] フィールドに新しい値を入力すると、 **ローカル** ウィンドウで、デバッグ パッケージ、文字列、式エバリュエーター \(EE\) を入力したとします。 EE は、この文字列は、関連付けられているローカルの単純な値、または式に含めることができ、結果として得られる値を評価します。  
  
 これは、ローカルの値を変更したプロセスの概要です。  
  
1.  新しい値を入力すると、Visual Studio は呼び出し [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 上、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 、ローカルの関連付けられているオブジェクト。  
  
2.  `IDebugProperty2::SetValueAsString` 次のタスクを実行します。  
  
    1.  値を生成する文字列を評価します。  
  
    2.  関連付けられたバインド [IDebugField](../../extensibility/debugger/reference/idebugfield.md) を取得するオブジェクト、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) オブジェクトです。  
  
    3.  一連のバイト値に変換します。  
  
    4.  呼び出し [値の代入](../Topic/IDebugObject::SetValue.md) デバッグ中のプログラムがアクセスできるように、値のバイトをメモリに配置します。  
  
3.  Visual Studio の更新、 **\[ローカル\]** 表示 \(を参照してください [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md) 詳細\)。  
  
 内の変数の値を変更するこの手順を使用しても、 **ウォッチ** ことを除けばウィンドウは、 `IDebugProperty2` の代わりに使用されるローカル変数の値に関連付けられているオブジェクト、 `IDebugProperty2` ローカル自体に関連付けられているオブジェクト。  
  
## このセクションの内容  
 [値の変更の実装のサンプル](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 MyCEE サンプルを使用して、順をおっての値を変更します。  
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [\[ローカル\] を表示します。](../Topic/Displaying%20Locals.md)