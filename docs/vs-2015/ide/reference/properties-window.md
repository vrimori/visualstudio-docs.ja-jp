---
title: プロパティ ウィンドウ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 88ff9388a7d23543a32368e763b5efb7abbdc8cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539280"
---
# <a name="properties-window"></a>[プロパティ] ウィンドウ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロパティ ウィンドウ](https://docs.microsoft.com/visualstudio/ide/reference/properties-window)します。  
  
  
このウィンドウで、エディターやデザイナーのオブジェクトを選択してデザイン時のプロパティやイベントを表示および変更できます。 また、**[プロパティ]** ウィンドウでは、ファイル、プロジェクト、およびソリューションのプロパティの編集や表示もできます。 **[プロパティ]** ウィンドウは **[表示]** メニューにあります。 また、F4 キーを押すか、**[クイック起動]** ウィンドウに「**プロパティ**」と入力して開くこともできます。  
  
 **[プロパティ]** ウィンドウでは、特定のプロパティの必要性に応じて、さまざまな編集フィールドを表示できます。 編集フィールドには、編集ボックス、ドロップダウン リスト、カスタム エディター ダイアログ ボックスへのリンクなどがあります。 淡色表示されているプロパティは読み取り専用です。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 [オブジェクト名]  
 現在選択しているオブジェクトが表示されます。 表示されるのは、アクティブなエディターまたはデザイナーのオブジェクトだけです。 複数のオブジェクトを選択すると、選択したすべてのオブジェクトに共通するプロパティだけが表示されます。  
  
 [項目別]  
 選択したオブジェクトのすべてのプロパティとプロパティ値がカテゴリ別に表示されます。 カテゴリを折りたたんで、表示されるプロパティ数を減らすことができます。 カテゴリを展開または折りたたむと、カテゴリ名の左側にプラス記号 (+) またはマイナス記号 (-) が表示されます。 カテゴリはアルファベット順に表示されます。  
  
 [アルファベット順]  
 選択したオブジェクトのデザイン時のプロパティおよびイベントがすべてアルファベット順に並べ替えられます。 淡色表示されていないプロパティを編集するには、セル内でプロパティの右側をクリックして、変更内容を入力します。  
  
 プロパティ ページ  
 選択した項目に対応する **[プロパティ ページ]** ダイアログ ボックスまたは **[プロジェクト デザイナー]** が表示されます。 [プロパティ ページ] には、**[プロパティ]** ウィンドウで使用できるプロパティのサブセット、同じプロパティ、またはプロパティのスーパーセットが表示されます。 このボタンを使用して、プロジェクトのアクティブな設定に関連するプロパティを表示および編集します。  
  
 プロパティ  
 オブジェクトのプロパティが表示されます。 **[プロパティ]** ウィンドウには、さまざまなオブジェクトのイベントも表示できます。  
  
 [プロパティ ソース別に並べ替え]  
 プロパティを、継承、適用されるスタイル、バインディングなどのソース別にグループ化します。 デザイナーでの XAML ファイルの編集時にのみ使用できます。  
  
 イベント  
 オブジェクトのイベントが表示されます。  
  
> [!NOTE]
>  **[プロパティ]** ウィンドウのこのツール バー コントロールを使用できるのは、フォーム デザイナーまたはコントロール デザイナーが [!INCLUDE[csprcs](../../includes/csprcs-md.md)] プロジェクトのコンテキストでアクティブなときに限られます。 XAML ファイルの編集時、イベントはプロパティ ウィンドウの別のタブに表示されます。  
  
 メッセージ  
 すべての Windows メッセージが表示されます。 選択したクラスに提供されたメッセージについて、指定されたハンドラー関数を追加または削除できます。  
  
> [!NOTE]
>  **[プロパティ]** ウィンドウのこのツール バー コントロールは、[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] プロジェクトのコンテキストで **[クラス ビュー]** がアクティブ ウィンドウになっているときだけ使用できます。  
  
 オーバーライド  
 選択したクラスのすべての仮想関数が表示され、オーバーライドする関数を追加または削除できます。  
  
> [!NOTE]
>  **[プロパティ]** ウィンドウのこのツール バー コントロールは、[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] プロジェクトのコンテキストで **[クラス ビュー]** がアクティブ ウィンドウになっているときだけ使用できます。  
  
 [説明ペイン]  
 プロパティの種類およびプロパティの簡単な説明が表示されます。 ショートカット メニューの [説明] コマンドを使用すると、プロパティの説明の表示と非表示を切り替えることができます。  
  
> [!NOTE]
>  **[プロパティ]** ウィンドウのこのツール バー コントロールは、デザイナーで XAML ファイルを編集しているときは使用できません。  
  
 [サムネイル ビュー]  
 デザイナーでの XAML ファイルの編集時に、現在選択されている要素のビジュアル表現を表示します。  
  
 検索  
 デザイナーでの XAML ファイルの編集時に、プロパティとイベントを検索するための機能を提供します。 検索ボックスは単語の一部の入力に反応し、入力すると検索結果が更新されます。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトのプロパティのリファレンス](../../ide/reference/project-properties-reference.md)   
 [ウィンドウ レイアウトをカスタマイズする](../../ide/customizing-window-layouts-in-visual-studio.md)



