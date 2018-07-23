---
title: ローカルの値を変更する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 788f496f2afeb3b6392cb165d243a9d83f8ea005
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151074"
---
# <a name="change-the-value-of-a-local"></a>ローカルの値を変更します。
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 値フィールドに新しい値を入力するときに、**ローカル**ウィンドウで、パッケージのデバッグ、文字列、ように入力すると、式エバリュエーター (EE)。 EE は、この文字列は、単純な値、または式に含めることができ、関連付けられているローカルを結果の値を評価します。  
  
 これは、ローカルの値を変更するプロセスの概要を示します。  
  
1.  新しい値を入力すると、Visual Studio は呼び出し[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)上、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)ローカルに関連付けられているオブジェクト。  
  
2.  `IDebugProperty2::SetValueAsString` では次のタスクを実行します。  
  
    1.  値を生成する文字列を評価します。  
  
    2.  関連付けられているバインド[IDebugField](../../extensibility/debugger/reference/idebugfield.md)オブジェクトを取得する、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)オブジェクト。  
  
    3.  一連のバイト値に変換します。  
  
    4.  呼び出し[SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md)デバッグ中のプログラムがアクセスできるように、メモリに、値のバイトを格納します。  
  
3.  Visual Studio の更新、**ローカル**表示 (を参照してください[表示の [ローカル]](../../extensibility/debugger/displaying-locals.md)詳細については)。  
  
 内の変数の値を変更するこの手順を使用しても、**ウォッチ**ウィンドウで、ある点を除く、`IDebugProperty2`の代わりに使用されるローカル変数の値に関連付けられているオブジェクト、`IDebugProperty2`オブジェクトに関連付けられたローカル自体。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [値を変更するサンプルの実装](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 値を変更するプロセスをステップ MyCEE サンプルを使用します。  
  
## <a name="see-also"></a>関連項目  
 [CLR の式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)