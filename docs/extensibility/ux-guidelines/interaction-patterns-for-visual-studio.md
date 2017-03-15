---
title: "Visual Studio の対話のパターン | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Visual Studio の対話のパターン
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## 概要  
 デザイン パターンでは、制約のようなセットに問題を解決するために特定の状況で適用できる設計の主要な一般です。 機能とシステムのデザイナーでは、これらのデザイン パターンを使用して出発点として、その特定の状況に適合させることができます。  
  
 Visual Studio には、新機能を構築する際に考慮すべき一般的な相互作用パターンのライブラリがあります。 デザイン パターンの 2 つの中核となるコンテキスト: Visual Studio クライアント \(devenv\) と Visual Studio Online です。 一部のデザインの問題については、すべての状況に適しているユビキタスなパターンがあります。 多くの場合、ただし、ソリューション異なる可能性があります、ブラウザーとクライアント アプリケーションでホストされていることに提示されている ui です。  
  
### Visual Studio クライアント パターンの種類  
  
|パターンの種類|説明|例|  
|-------------|--------|-------|  
|**アプリケーション レベルのパターン**|高度なパターンを決定する、またはアプリケーションのコンテキストを表示してそこに含まれる複合デバイスとコントロール パターンを含む、アプリケーションに共通|-   ツール ウィンドウ<br />-   ドキュメント ウィンドウ|  
|**合成パターン**|アプリケーションのパターンにわたる可能性がある一般的なパターンまたは個別の構成ではいくつかのコントロールで構成されて認識されているパターン|-   ビューの切り替え<br />-   リスト ビルダー<br />-   データを表示します。<br />-   通知<br />-   検証<br />-   モデルの選択|  
|**コントロール パターン**|どのように低レベルのコントロールについての詳細が動作するが予測します。|-   ツリー ビュー<br />-   グリッド コントロール内での編集|  
  
## アプリケーション パターン  
 大まかに言えば、Visual Studio インターフェイスには、複数のウィンドウ、ダイアログ ボックス、コマンド、および 1 つの IDE 内でツールバーが構成されています。 Visual Studio の階層では、コンテキストとドライブのメニューを決定します。 IDE のユーザー インターフェイスの主な統合ポイントがドキュメント ウィンドウ、ツール ウィンドウ、プロジェクト、コマンドの構造、テキスト エディター、ツールボックス、\[プロパティ\] ウィンドウおよびツール \> オプションです。  
  
 各 IDE のユーザー インターフェイスの主な統合ポイントの基本的な使用パターンがあります。  
  
-   [メニューと Visual Studio のコマンド](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Visual Studio のアプリケーション パターン](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [ウィンドウの相互作用](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [ツール ウィンドウ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [ドキュメントのエディターの表記規則](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [ダイアログ ボックス](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [プロジェクト](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## 一般的なコントロール パターン  
 コントロール パターンは、個別のコントロールの概要として予想される動作は主にします。 これは、一貫性の最も重要な領域の 1 つです。  
  
 Visual Studio での最も一般的なコントロールは、デスクトップ Windows ガイドラインに従う必要があります。 当社のガイドラインには、Visual Studio 固有の相互作用、または場所をよりも優先ガイドライン全体を高度なユーザーのニーズを満たすために Visual Studio をカスタマイズするために共通の規則を強化することが必要になる領域にはのみが含まれます。  
  
-   [Visual Studio の一般的なコントロール パターン](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [コモン コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [テキスト コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [ボタンやハイパーリンク](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## 合成パターン  
 さまざまなタスクを実行するユーザーが予想される方法があります。 可能な限り、相互作用と視覚的なデザインの両方に対して、これらのパターンを使用する機能を設計する必要があります。  
  
 いくつかの最も重要な Visual Studio 内で複数の複合パターンがあるときに整合性に関しては。  
  
-   [Visual Studio の複合パターン](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [オブジェクトの UI およびピークする方法](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [モデルの選択](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [永続化と設定の保存](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [タッチ入力](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)