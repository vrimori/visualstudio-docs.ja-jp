---
title: "ローカルの値を変更する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03e6acb4ee9756d0bbb14a6e3667375d32cafba9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-value-of-a-local"></a>ローカルの値を変更します。
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 値フィールドに新しい値を入力するときに、**ローカル**ウィンドウで、デバッグ パッケージ文字列を渡します、式エバリュエーター (EE) を入力したとします。 EE は、この文字列は、単純な値または式を含めることができ、関連付けられているローカルの結果として得られる値を格納するを評価します。  
  
 これは、ローカルの値を変更するプロセスの概要です。  
  
1.  新しい値を入力すると、Visual Studio は呼び出し[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)上、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)ローカルに関連付けられているオブジェクト。  
  
2.  `IDebugProperty2::SetValueAsString`次のタスクを実行します。  
  
    1.  値を生成するために文字列を評価します。  
  
    2.  関連付けられたバインド[IDebugField](../../extensibility/debugger/reference/idebugfield.md)を取得するオブジェクト、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)オブジェクト。  
  
    3.  一連のバイト値に変換します。  
  
    4.  呼び出し[SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md)デバッグ中のプログラムがアクセスできるように、メモリに値のバイトを格納します。  
  
3.  Visual Studio の更新、**ローカル**表示 (を参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)詳細については)。  
  
 このプロシージャは、内の変数の値を変更するのには使用も、**ウォッチ**それ以外のウィンドウが、`IDebugProperty2`の代わりに使用されるローカル変数の値に関連付けられているオブジェクト、`IDebugProperty2`ローカルに関連付けられているオブジェクトできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [値の変更の実装のサンプル](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 値を変更するプロセスをステップ MyCEE サンプルを使用します。  
  
## <a name="see-also"></a>参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)