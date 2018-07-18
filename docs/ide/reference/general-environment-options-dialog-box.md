---
title: '[全般]\([オプション] ダイアログ ボックス - [環境])'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f12249cc8d0e8bd8396e1e1ebbbfefeddbb22b60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948130"
---
# <a name="general-environment-options-dialog-box"></a>[全般]\([オプション] ダイアログ ボックス - [環境])

このページを使用して、統合開発環境 (IDE: Integrated Development Environment) のオプションのうち特に配色テーマ、ステータス バーの設定、およびファイル拡張子の関連付けを変更します。 **[オプション]** ダイアログ ボックスを表示するには、**[ツール]** メニューを開いて、**[オプション]** をクリックし、**[環境]** フォルダーを開き、**[全般]** ページをクリックします。 このページが一覧に表示されない場合は、**[オプション]** ダイアログ ボックスの **[すべての設定を表示]** チェック ボックスをオンにします。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、**[ツール]** メニューを開き、**[設定のインポートとエクスポート]** を選択します。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="visual-experience"></a>視覚的効果

**[配色テーマ]**

IDE の配色テーマで **[青]**、**[淡色]** または **[濃色]** を選択します。

[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) から **Visual Studio 配色テーマ エディター**をダウンロードしインストールすることで、定義済みテーマを追加でインストールしたりカスタム テーマを作成したりすることもできます。 このツールをインストールすると、追加の配色テーマが [配色テーマ] ボックスの一覧に表示されます。

**メニュー バーにタイトルの文字種を適用する**

既定では、メニューは**タイトルの文字種**になります。 このオプションのチェック ボックスをオフにすると、メニューが**すべて大文字**に設定されます。

**クライアントのパフォーマンスに基づいて視覚的効果を自動的に調整する**

Visual Studio で視覚的効果を自動的に調整するか、ユーザーが明示的に調整するかを指定します。 この調整によって、色の表示がグラデーションからフラットに変わったり、メニューまたはポップアップ ウィンドウでのアニメーションの使用が制限されたりすることがあります。

**リッチ クライアント エクスペリエンスを有効にする**

グラデーションやアニメーションなど、Visual Studio の視覚的効果のすべてを有効にします。 リモート デスクトップ接続や古いグラフィックス アダプターを使用している場合は、これらの機能のパフォーマンスが低下する可能性があるため、このオプションをオフにします。 このオプションをオンにできるのは、**[クライアントのパフォーマンスに基づいて視覚的効果を自動的に調整する]** をオフにした場合だけです。

**可能ならハードウェアのグラフィックス アクセラレータを使用する**

可能な場合は、ソフトウェア アクセラレータではなく、ハードウェアのグラフィックス アクセラレータを使用します。

## <a name="other"></a>その他

**項目をウィンドウ メニューに表示**

**[ウィンドウ]** メニューの [ウィンドウ] の一覧に表示されるウィンドウ数をカスタマイズします。 1 ～ 24 の値を入力します。 既定値は 10 です。

**項目を最近使用した一覧に表示**

**[ファイル]** メニューに表示される、最近使ったプロジェクトとファイルの数をカスタマイズします。 1 ～ 24 の値を入力します。 既定値は 10 です。 このオプションを使用すると、最近使用したプロジェクトやファイルを簡単に表示できます。

**ステータス バーの表示**

ステータス バーが表示されます。 ステータス バーは IDE ウィンドウの一番下にあり、処理中の操作の進行状況が表示されます。

**[閉じる] ボタンを、アクティブなツール ウィンドウに対してのみ実行する**

**[閉じる]** をクリックしたときに、ドッキング セット内のすべてのツール ウィンドウではなく、フォーカスのあるツール ウィンドウだけを閉じるように指定します。 既定では、このチェック ボックスはオンになっています。

**[自動的に隠す] ボタンを、アクティブなツール ウィンドウに対してのみ実行する**

**[自動的に隠す]** をクリックしたときに、ドッキング セット内のすべてのツール ウィンドウではなく、フォーカスのあるツール ウィンドウだけを自動的に非表示にするように指定します。 既定では、このチェック ボックスはオフになっています。

## <a name="see-also"></a>関連項目

- [[環境] ([オプション] ダイアログ ボックス)](../../ide/reference/environment-options-dialog-box.md)
- [ウィンドウ レイアウトをカスタマイズする](../../ide/customizing-window-layouts-in-visual-studio.md)