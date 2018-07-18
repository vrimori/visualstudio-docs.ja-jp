---
title: Visual Studio の相互作用のパターン |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142433"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio の相互作用のパターン
## <a name="overview"></a>概要  
 デザイン パターンは、制約の類似のセットの問題を解決するために特定の状況で適用できる設計のコアを一般です。 機能およびシステム デザイナーは、出発点として、その特定の状況に合わせて変更できるこれらの設計パターンを使用します。  
  
 Visual Studio には、新機能を構築するときに考慮すべき一般的な相互作用のパターンのライブラリがあります。 デザイン パターンを 2 つの主要なコンテキストがある: Visual Studio クライアント (devenv) および Visual Studio Online です。 デザイン問題の種類によって、すべての状況でも動作する場所を問わずパターンがあります。 多くの場合、ただし、ソリューション異なる可能性があります、ブラウザーとクライアント アプリケーションでホストされている内で提示されている UI。  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio クライアント パターンの種類  
  
|パターンの種類|説明|使用例|  
|------------------|-----------------|--------------|  
|**アプリケーション レベルのパターン**|高度なパターンを決定する、またはアプリケーションのコンテキストを表示してそれらに含まれる複合とコントロール パターンを含む、アプリケーションに共通する|ツール ウィンドウ<br />ドキュメント ウィンドウ|  
|**合成パターン**|アプリケーション パターンでは、全体にわたる場合がありますの一般的なパターンまたは個別の構成で複数のコントロールから成る認識されているパターン|ビューの切り替え<br />リスト ビルダー<br />データを表示します。<br />-通知<br />検証<br />モデルの選択|  
|**コントロール パターン**|動作にどのように低レベルの制御についての詳細が必要|ツリー ビュー<br />グリッド コントロール内で編集|  
  
## <a name="application-patterns"></a>アプリケーション パターン  
 大まかに言えばは、Visual Studio のインターフェイスは、複数の windows、ダイアログ ボックス、コマンド、および 1 つの IDE 内でツールバーを構成します。 Visual Studio の階層では、コンテキストとドライブ、コンテキスト メニューを決定します。 IDE のユーザー インターフェイスでキーの統合ポイントはドキュメント ウィンドウ、ツール ウィンドウ、プロジェクト、コマンドの構造、テキスト エディター、ツールボックス、[プロパティ] ウィンドウおよびツール > オプション。  
  
 各 IDE のユーザー インターフェイスでキーの統合ポイントの基本的な使用パターンがあります。  
  
-   [Visual Studio のメニューとコマンド](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Visual Studio のアプリケーション パターン](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [ウィンドウの相互作用](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [ツール ウィンドウ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [ドキュメント エディターの表記規則](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [ダイアログ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [プロジェクト](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>共通のコントロール パターン  
 コントロール パターンは、主に動作する個別のコントロールの概要が必要です。 これは、整合性の最も重要な 1 つの領域です。  
  
 Visual Studio での最も一般的なコントロールは、デスクトップの Windows のガイドラインに従う必要があります。 ガイドラインには、Visual Studio 固有の相互作用と場所をお置き換えるガイドライン全体を高度なユーザーのニーズを満たすために Visual Studio をカスタマイズするために共通の規約を強化することが必要になる領域にはのみが含まれます。  
  
-   [Visual Studio の コモン コントロール パターン](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [コモン コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [テキスト コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [ボタンとハイパーリンク](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>合成パターン  
 さまざまなタスクを実行するユーザーが予想される方法があります。 可能な限り、これらのパターンの相互作用とビジュアル デ ザインの両方を使用する機能を設計する必要があります。  
  
 いくつかの最も重要な Visual Studio 内の多くの複合パターンがあるときに整合性に関しては。  
  
-   [Visual Studio の複合パターン](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [オブジェクトの UI およびピークする方法](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [モデルの選択](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [永続化と設定を保存します。](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [タッチ入力](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)