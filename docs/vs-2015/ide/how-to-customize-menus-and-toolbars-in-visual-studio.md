---
title: '方法: メニューおよびツール バーをカスタマイズする'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b492764c6d872ff8f2568b4abcbeefe133ee23c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795434"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>方法: Visual Studio でメニューおよびツール バーをカスタマイズする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio は、メニュー バーでツール バーやメニューを追加および削除するだけでなく、任意のツール バーまたはメニューでコマンドを追加および削除することによってもカスタマイズできます。

> [!WARNING]
>  ツール バーまたはメニューをカスタマイズした後、該当するチェック ボックスが **[カスタマイズ]** ダイアログ ボックスでオンになっていることを確認してください。 オンになっていない場合、Visual Studio を閉じて再度開くと、変更は保持されません。

 **このトピックの内容**

-   [メニュー バーでのメニューの追加、削除、または移動](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)

-   [ツール バーの追加、削除、または移動](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)

-   [メニューまたはツール バーのカスタマイズ](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)

-   [メニューまたはツール バーのリセット](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)

##  <a name="bkmk_addmenu"></a>メニュー バーでのメニューの追加、削除、または移動

1.  メニュー バーから **[ツール]**、**[カスタマイズ]** の順に選びます。

     **[カスタマイズ]** ダイアログ ボックスが開きます。

2.  **[コマンド]** タブで、**[メニュー バー]** をオンのままにし、その横のオプションにあるリストで **[メニュー バー]** をオンのままにして、次のいずれかの手順を実行します。

    -   メニューを追加するには、**[新しいメニューの追加]** を選び、**[選択内容の編集]** ボタンを選んで、追加するメニューに名前を付けます。

         ![メニューの追加方法を表示するダイアログ ボックスをカスタマイズ](../ide/media/addmenu.png "AddMenu")

    -   メニューを削除するには、**[コントロール]** の一覧で削除するメニューを選び、**[削除]** を選びます。

    -   メニュー バー内でメニューを移動するには、**[コントロール]** の一覧でメニューを選び、**[上へ移動]** または **[下へ移動]** ボタンを選びます。

##  <a name="bkmk_addtoolbar"></a>ツール バーの追加、削除、または移動

1.  メニュー バーから **[ツール]**、**[カスタマイズ]** の順に選びます。

     **[カスタマイズ]** ダイアログ ボックスが開きます。

2.  **[ツール バー]** タブで、次のいずれかの手順を実行します。

    -   ツール バーを追加するには、**[新規]** を選び、追加するツール バーの名前を指定して、**[OK]** ボタンを選びます。

         ![ツールバーの追加方法を表示するダイアログ ボックスをカスタマイズ](../ide/media/addtoolbar.png "AddToolbar")

    -   カスタム ツール バーを削除するには、**[ツール バー]** の一覧で削除するツール バーを選び、**[削除]** ボタンを選びます。

        > [!IMPORTANT]
        >  ユーザーが作成したツール バーは削除できますが、既定のツール バーは削除できません。

    -   ツール バーを別のドッキング位置に移動するには、**[ツール バー]** の一覧で該当するツール バーを選び、**[選択内容の編集]** ボタンを選んで、表示された一覧から位置を選びます。

         また、ツール バーの左端をドラッグして、メイン ドッキング領域内の任意の場所に移動することもできます。

        > [!NOTE]
        >  ツール バーの操作性とアクセシビリティを向上させる方法の詳細については、「[方法:IDE アクセシビリティ オプションを設定する](../ide/reference/how-to-set-ide-accessibility-options.md)」を参照してください。

##  <a name="bkmk_customize"></a> メニューまたはツール バーのカスタマイズ

1.  メニュー バーから **[ツール]**、**[カスタマイズ]** の順に選びます。

     **[カスタマイズ]** ダイアログ ボックスが開きます。

2.  **[コマンド]** タブで、カスタマイズする要素の種類に対応するオプション ボタンを選びます。

3.  要素の種類の一覧で、カスタマイズするメニューまたはツール バーを選択し、次のいずれかの手順を実行します。

    -   コマンドを追加するには、**[コマンドの追加]** を選びます。

         **[コマンドの追加]** ダイアログ ボックスの **[カテゴリ]** の一覧で項目を選んだ後、**[コマンド]** の一覧で項目を選んで、**[OK]** ボタンを選びます。

         ![Visual Studio の [コマンドの追加] ダイアログ ボックス](../ide/media/addcommand.png "AddCommand")

    -   コマンドを削除するには、**[コントロール]** の一覧で削除するコマンドを選び、**[削除]** ボタンを選びます。

    -   コマンドの順序を変更するには、**[コントロール]** の一覧でコマンドを選び、**[上へ移動]** または **[下へ移動]** ボタンを選びます。

    -   コマンドをグループに区切るには、**[コントロール]** の一覧でコマンドを選び、**[選択内容の編集]** ボタンを選んだ後、表示されたメニューで **[グループの始まり]** を選びます。

##  <a name="bkmk_reset"></a> メニューまたはツール バーのリセット

1.  メニュー バーから **[ツール]**、**[カスタマイズ]** の順に選びます。

     **[カスタマイズ]** ダイアログ ボックスが開きます。

2.  **[コマンド]** タブで、リセットする要素の種類に対応するオプション ボタンを選びます。

3.  要素の種類の一覧で、リセットするメニューまたはツール バーを選択します。

4.  **[選択内容の編集]** ボタンを選び、表示されたメニューで **[リセット]** を選びます。

     また、**[すべてリセット]** ボタンを選んで、すべてのメニューおよびツール バーをリセットできます。
