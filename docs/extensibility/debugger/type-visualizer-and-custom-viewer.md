---
title: ビジュアライザーとカスタム ビューアー入力 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0879d18922e730d9cd737bdefde52576b6b03638
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948564"
---
# <a name="type-visualizer-and-custom-viewer"></a>型のビジュアライザーとカスタム ビューアー
型のビジュアライザーは、特定の形式でデータの一部を表示するコンポーネントです。 形式が完全には、ビジュアライザーを実装するまでは、エンドユーザーまたはビジュアライザーのサード パーティ サプライヤーです。  
  
 カスタム ビューアーは、特定の形式でデータの一部を表示するカスタム式エバリュエーターの一部です。 この形式では、カスタム ビューアー、形式が、式の評価 (EE) の実装者であることを意味の実行者に完全に依存します。  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>式エバリュエーターの種類のビジュアライザーのサポート  
 EE ビジュアライザーにアクセスできるインターフェイスのセットをサポートすることによって型のビジュアライザーをサポートしています: ようなインターフェイス[IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)と[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)します。 ただし、EE はビジュアライザーの型自体を実装する必要はありません: EE だけが許可外部ビジュアライザーの型情報にアクセスします。 このようなビジュアライザーが、EE に同梱され、Visual Studio、またはエンドユーザーによっても、他のサード パーティ ベンダーによって提供の適切な場所にインストールされています。  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>式エバリュエーターでのカスタム ビューアーのサポート  
 EE は EE 自体がデータ型を表示するためのコードを提供するカスタム ビューアーもサポートできます。 カスタム ビューアーを実装して、 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)インターフェイスで、どのような形式でデータを表示するすべての職務の処理が必要な場合、ビューアーが完全に制御、表示と変更データもことができます。 製品に付属しているときに、EE によって提供される任意のカスタム ビューアーで、EE が付属します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)   
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)