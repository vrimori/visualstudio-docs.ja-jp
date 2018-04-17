---
title: コマンドを Vspackage でルーティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58be191a3b7a2256d0883e313f77b264f6be4d69
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="command-routing-in-vspackages"></a>Vspackage でルーティング コマンド
コマンドがルーティングされる[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]が実行コンテキストに基づきます。 外側の初期コンテキストからグローバル コンテキストにルーティングされます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)  
 コマンド ルーティングの解像度の順序について説明します。  
  
 [可用性](../../extensibility/internals/command-availability.md)  
 コマンド ルーティングについて説明します。  
  
 [相互運用機能アセンブリを使用するコマンドとメニュー](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 マネージ コードと COM の間のルーティングのコマンドでの考慮事項について説明します  
  
## <a name="related-sections"></a>関連項目  
 [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)  
 ウィンドウ上では、ユーザーの選択コンテキストのフォーカスを判断する方法のモデルについて説明します。  
  
 [コマンド、メニュー、およびツール バー](../../extensibility/internals/commands-menus-and-toolbars.md)  
 メニュー、ツール バー、およびコマンド コンボ ボックスが含まれている UI を作成する方法について説明します。