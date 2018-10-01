---
title: ビジュアライザーとカスタム ビューアー入力 |Microsoft Docs
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
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d347e7b18722aa8f8901abac3966150b3dca97cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535973"
---
# <a name="type-visualizer-and-custom-viewer"></a>型のビジュアライザーとカスタム ビューアー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[型のビジュアライザーとカスタム ビューアー](https://docs.microsoft.com/visualstudio/extensibility/debugger/type-visualizer-and-custom-viewer)します。  
  
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

