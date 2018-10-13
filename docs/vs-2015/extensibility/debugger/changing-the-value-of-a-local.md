---
title: ローカルの値を変更する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcdefc93f8d9843ac18a01f52e9c2a36f59ce4ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226214"
---
# <a name="changing-the-value-of-a-local"></a>ローカルの値の変更
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
3.  Visual Studio の更新、**ローカル**表示 (を参照してください[を表示するローカル](../../extensibility/debugger/displaying-locals.md)詳細については)。  
  
 内の変数の値を変更するこの手順を使用しても、**ウォッチ**それ以外のウィンドウは、`IDebugProperty2`の代わりに使用されるローカル変数の値に関連付けられているオブジェクト、`IDebugProperty2`オブジェクトに関連付けられたローカル自体。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [値の変更の実装のサンプル](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 値を変更するプロセスをステップ MyCEE サンプルを使用します。  
  
## <a name="see-also"></a>関連項目  
 [CLR の式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [ローカルの表示](../../extensibility/debugger/displaying-locals.md)

