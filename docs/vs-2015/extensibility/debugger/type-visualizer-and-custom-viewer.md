---
title: ビジュアライザーとカスタム ビューアー入力 |Microsoft Docs
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
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5319721d57212f4fc853ca99c1544a51d4af878c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732131"
---
# <a name="type-visualizer-and-custom-viewer"></a>型のビジュアライザーとカスタム ビューアー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

型のビジュアライザーは、非常に特定の形式でデータの一部を表示するコンポーネントです。 この形式は、ビジュアライザーの実行者責任を持って、エンド ユーザーやサード パーティ サプライヤーのビジュアライザーです。  
  
 カスタム ビューアーは、非常に特定の形式でデータの一部を表示するカスタム式エバリュエーターの一部です。 この形式では、カスタム ビューアー、形式が、式の評価 (EE) の実装者であることを意味の実行者に完全に依存します。  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>式エバリュエーターの種類のビジュアライザーのサポート  
 ビジュアライザーにアクセスできるインターフェイスのセットをサポートすることによって型のビジュアライザーをサポートできる、EE: ようなインターフェイス[IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)と[IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)します。 ただし、EE は、ビジュアライザーの型自体を実装する責任を負いますされません: EE だけが許可外部ビジュアライザーの型情報にアクセスします。 このようなビジュアライザーが、EE に同梱され、Visual Studio、またはエンドユーザーによっても、他のサード パーティ ベンダーによって提供の適切な場所にインストールされています。  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>式エバリュエーターでのカスタム ビューアーのサポート  
 EE は EE 自体がデータ型を表示するためのコードを提供するカスタム ビューアーもサポートできます。 カスタム ビューアーを実装して、 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)インターフェイスで、どのような形式でデータを表示するすべての職務の処理が必要な場合、ビューアーの表示を完全に制御しでもデータの変更を許可することができます。 製品に付属しているときに、EE によって提供される任意のカスタム ビューアーで、EE が付属します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)   
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

