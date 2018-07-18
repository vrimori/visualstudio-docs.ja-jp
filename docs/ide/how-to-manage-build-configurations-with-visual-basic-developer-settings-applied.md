---
title: '方法 : Visual Basic 開発者設定が適用されたビルド構成を管理する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 987419e62d54b44a21a70f625e2a240bd7aecc21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946261"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>方法 : Visual Basic 開発者設定が適用されたビルド構成を管理する

既定では、すべてのビルド構成の詳細オプションは Visual Studio 開発者設定が適用されて非表示になっています。 このトピックでは、これらの設定を手動で有効にする方法について説明します。

## <a name="enable-advanced-build-configurations"></a>ビルド構成の詳細を有効にする

既定では、**[構成マネージャー]** ダイアログ ボックスおよび[プロジェクト デザイナー](..//ide/reference/application-page-project-designer-visual-basic.md)の **[構成]** 一覧と **[プラットフォーム]** 一覧を開くためのオプションは、Visual Basic 開発者設定によって非表示になっています。

1.  **[ツール]** メニューの **[オプション]** をクリックします。

2.  **[プロジェクトおよびソリューション]** を展開し、**[全般]** をクリックします。

    > [!NOTE]
    > **[全般]** ノードは、**[すべての設定を表示]** オプションがオフになっている場合でも表示されます。 使用可能なすべてのオプションを表示する場合は、**[すべての設定を表示]** をクリックします。

3.  **[ビルド構成の詳細を表示]** をクリックします。

4.  **[OK]** をクリックします。

     **[ビルド]** メニューで **[構成マネージャー]** を使用できるようになり、**[構成]** 一覧と **[プラットフォーム]** 一覧が**プロジェクト デザイナー**に表示されるようになります。

## <a name="see-also"></a>関連項目

- [ビルド構成について](../ide/understanding-build-configurations.md)
- [コンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)