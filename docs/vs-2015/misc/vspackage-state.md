---
title: VSPackage の状態 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: douge
ms.openlocfilehash: 1fee544dcf9bec9295d297f153df7f86dd464bda
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192856"
---
# <a name="vspackage-state"></a>Visual Studio の状態
多くの要因の永続化された値、または状態のセットを特定するため、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]アプリケーション。  
  
-   プロジェクトでは、プロジェクトと構成のプロパティがあります。  
  
-   ソリューションでは、プロパティがあります。  
  
-   ユーザー設定は、ドキュメント ウィンドウ、ツール ウィンドウ、ドッキング状態、およびキーボード ショートカットの位置とサイズを決定します。  
  
-   アプリケーションには、ユーザー設定オプションのことができます。  
  
-   アプリケーションが作成されるオブジェクトは、独自のプロパティを持つことができます。  
  
 次の方法を[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]アプリケーションの状態を管理できます。  
  
-   プロジェクトとソリューションのプロパティ ページ。  
  
-   を通じて、**インポートおよびエクスポート設定ウィザード**ユーザーが 1 台のコンピューターから別の設定を移動できます。  
  
-   を通じて、**オプション** ダイアログ ボックスで、アプリケーションに関連するオプションが含まれています。  
  
-   を通じて、**プロパティ**ウィンドウで、オブジェクトのプロパティを公開します。  
  
-   自動化します。 アプリケーションは、オートメーションに公開されている VSPackage とオブジェクトのプロパティにアクセスできます。  
  
 アプリケーションの状態を基になるとは、アプリケーションの状態を保存して復元を有効にする各種の永続化メカニズムです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [状態の永続性のサポート](../misc/support-for-state-persistence.md)  
 VSPackage の状態を保存、復元、リセットするための一般的な戦略を一覧表示します。  
  
 [オプションとオプション ページ](../extensibility/internals/options-and-options-pages.md)  
 標準とカスタム オプション ページを紹介し、それらを実装する方法について説明します。  
  
 [オプション ページの作成](../extensibility/creating-an-options-page.md)  
 2 つのオプション ページ、単純なページおよびカスタム ページを作成する方法について説明します。  
  
 [設定カテゴリのサポート](../misc/support-for-settings-categories.md)  
 ユーザー設定と、作成し、永続化の方法について説明します。  
  
 [設定カテゴリの作成](../extensibility/creating-a-settings-category.md)  
 作成する方法について説明します、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]設定カテゴリに値を保存し、値の設定ファイルからの復元に使用します。  
  
 [プロパティとプロパティ ウィンドウの拡張](../extensibility/extending-properties-and-the-property-window.md)  
 内のオブジェクトの値を変更および表示する方法について説明します、**プロパティ**ウィンドウ。  
  
 [プロパティ ウィンドウへのプロパティの公開](../extensibility/exposing-properties-to-the-properties-window.md)  
 オブジェクトのパブリック プロパティを公開する方法について説明します、**プロパティ**ウィンドウ。  
  
 [プロジェクトおよび構成プロパティのサポート](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 プロジェクトと構成のプロパティを表示および変更方法について説明します。  
  
 [プロジェクト プロパティの取得](../extensibility/getting-project-properties.md)  
 ツール ウィンドウで、プロジェクトのプロパティを表示するマネージ VSPackage を作成する手順について説明します。  
  
 [設定ストアの使用](../extensibility/using-the-settings-store.md)  
 設定ストアの永続化メカニズムとその使用方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)  
 作成して、Vspackage を使用する方法を説明するトピックへの一般的な方向を提供します。