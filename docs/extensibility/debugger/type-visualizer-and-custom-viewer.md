---
title: "ビジュアライザーとカスタム ビューアー入力 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80798887beee6116b3a93b5d8ec86b14269b5475
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="type-visualizer-and-custom-viewer"></a>型のビジュアライザーとカスタム ビューアー
型のビジュアライザーは、非常に特定の形式でデータを表示するコンポーネントです。 この形式は、ビジュアライザーの実行者の次第、エンドユーザーまたはビジュアライザー サード パーティ製品を供給します。  
  
 カスタム ビューアーは、非常に特定の形式でデータを表示するカスタム式エバリュエーターの一部です。 この形式では、つまり形式は、式の評価 (EE) の実装者は、カスタム ビューアーの実行者の次第です。  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>式エバリュエーターの種類のビジュアライザーのサポート  
 ビジュアライザーにアクセスできるインターフェイスのセットをサポートすることにより、EE が型のビジュアライザーをサポートできます: ようなインターフェイス[IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)と[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)です。 ただし、EE がそれ自体の種類のビジュアライザーを実装する責任がないこと: EE だけを実行により、外部のビジュアライザーの型情報へのアクセス。 このようなビジュアライザーを EE と共に出荷されたおよび他のサード パーティ ベンダーまたはエンドユーザーによっても提供している Visual Studio での適切な場所にインストールされている可能性があります。  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>式エバリュエーターでのカスタム ビューアーのサポート  
 EE は、EE 自体が、データ型を表示するためのコードを提供するカスタム ビューアーにもサポートできます。 カスタム ビューアーを実装して、 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)どのような形式でデータを表示するすべての職務を処理するインターフェイスが必要な以外の場合は、ビューアーの表示を完全に制御があり、変更するデータを許可することができますも。 EE によって提供される任意のカスタム ビューアーは、製品に付属しているときに、EE が付属します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー コンポーネント](../../extensibility/debugger/debugger-components.md)   
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)