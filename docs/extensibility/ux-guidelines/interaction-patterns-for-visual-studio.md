---
title: Visual Studio のインタラクション パターン |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7066b9b5968aaaae2bbf608ee9f56e9c4bcf07e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862954"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio のインタラクション パターン
## <a name="overview"></a>概要  
 設計パターンは、制約の類似のセットに関する問題を解決するために特定の状況で適用できる設計のコアを一般に、です。 機能およびシステム デザイナーは、開始点で、その特定の状況に適応できますとしてこれらの設計パターンを使用します。  
  
 Visual Studio では、新しい機能を構築する際に考慮すべき一般的な相互作用パターンのライブラリには。 これには、デザイン パターンの 2 つのコアのコンテキストがあります。Visual Studio クライアント (devenv) と Visual Studio Online。 一部のデザインの問題については、すべての状況に適しているユビキタス パターンがあります。 多くの場合、ただし、ソリューション、異なる可能性があります UI 内で、ブラウザーとクライアント アプリケーションでホストされているが提示されています。  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio クライアント パターンの種類  
  
|パターンの種類|説明|使用例|  
|------------------|-----------------|--------------|  
|**アプリケーション レベルのパターン**|高度なパターンを決定する、またはアプリケーションのコンテキストを表示してそれらに含まれる複合デバイスとコントロール パターンを含む、アプリケーションに共通|-ツール ウィンドウ<br />ドキュメント ウィンドウ|  
|**コンポジット パターン**|アプリケーションのパターンにわたる可能性がある一般的なパターンまたは認識されているパターンの個別の構成でいくつかのコントロールで構成されます。|ビューの切り替え<br />リスト ビルダー<br />-データを表示します。<br />-通知<br />検証<br />モデルの選択|  
|**コントロール パターン**|どのように低レベルのコントロールについての詳細が動作する必要があります。|ツリー ビュー<br />グリッド コントロール内で編集|  
  
## <a name="application-patterns"></a>アプリケーション パターン  
 大まかに言えばは、Visual Studio のインターフェイスは、複数の windows、ダイアログ ボックス、コマンド、および 1 つの IDE 内でツールバーを構成します。 Visual Studio の階層には、コンテキストとドライブのメニューが決定します。 IDE のユーザー インターフェイスの主な統合ポイントがドキュメント ウィンドウ、ツール ウィンドウ、プロジェクト、コマンドの構造、テキスト エディター、ツールボックス、[プロパティ] ウィンドウおよびツール > オプション。  
  
 各 IDE のユーザー インターフェイスの主な統合ポイントの基本的な使用パターンがないです。  
  
-   [Visual Studio のメニューとコマンド](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Visual Studio のアプリケーション パターン](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [ウィンドウの相互作用](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [ツール ウィンドウ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [ドキュメント エディターの表記規則](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [ダイアログ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [プロジェクト](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>コモン コントロール パターン  
 コントロール パターンは、主に動作する個別のコントロールの概要が必要です。 これは、一貫性の最も重要な領域の 1 つです。  
  
 Visual Studio での最も一般的なコントロールは、デスクトップ Windows ガイドラインに従う必要があります。 当社のガイドラインには、Visual Studio に固有の相互作用、または場所を置き換えるガイドライン全体を高度なユーザーのニーズを満たすために Visual Studio を調整するために一般的な規則を強化することが必要になる領域にはのみが含まれます。  
  
-   [Visual Studio の コモン コントロール パターン](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [コモン コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [テキスト コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [ボタンやハイパーリンク](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>コンポジット パターン  
 さまざまなユーザー タスクを実行することを期待する方法があります。 可能な限り、これらのパターンは、相互作用とビジュアル デザインの両方を使用する機能を設計する必要があります。  
  
 いくつかの最も重要な Visual Studio 内の多くの複合パターンがありますが、整合性に関して。  
  
-   [Visual Studio の複合パターン](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [オブジェクトの UI とピークします。](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [モデルの選択](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [永続化と設定の保存](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [タッチ入力](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)