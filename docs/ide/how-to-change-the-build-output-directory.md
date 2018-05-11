---
title: '方法 : ビルド出力ディレクトリを変更する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 721b8241a3278ddbf1be3b5477e8829b7aa4447b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-build-output-directory"></a>方法 : ビルド出力ディレクトリを変更する

プロジェクトによって生成された (デバッグ、リリース、またはその両方の) 構成ごとに出力の場所を指定できます。

> [!NOTE]
> **セットアップ** プロジェクトがある場合は、この記事の最後にあるメモを参照してください。

## <a name="change-the-build-output-directory"></a>ビルド出力ディレクトリを変更する

1.  メニュー バーで、**[プロジェクト]** > **[\<アプリケーション名>] > [プロパティ]** の順に選択します。 **ソリューション エクスプローラー** でプロジェクト ノードを右クリックし、 **[プロパティ]** をクリックすることもできます。

2.  Visual Basic プロジェクトの場合は、 **[コンパイル]** タブを選択します。C# プロジェクトの場合は、**[ビルド]** タブを選択します。C++ プロジェクトまたは JavaScript プロジェクトの場合は、 **[全般]** タブを選択します。

3.  上部にある構成のドロップダウンで、出力ファイルの場所を変更する構成を選択します (デバッグ、リリース、またはすべて)。

     出力パスのエントリを検索します (Visual Basic の場合は **[ビルド出力パス]**、Visual C++ の場合は **[出力ディレクトリ]**、JavaScript と C# の場合は **[出力パス]**)。 プロジェクト ディレクトリを基準として相対的に新しいビルド出力ディレクトリを指定します。

> [!NOTE]
> セットアップ プロジェクトの **[出力ファイル名]** ボックスでは、プロジェクト ファイルの場所ではなく、*Setup.exe* ファイルの場所のみを変更します。 詳細については、「**Build, Configuration Properties, Deployment Project Properties dialog box**」(配置プロジェクトの [プロパティ ページ] ダイアログ ボックス ([構成プロパティ] - [ビルド])) を参照してください。

## <a name="see-also"></a>関連項目

- [[ビルド] ページ (プロジェクト デザイナー) (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [[全般] プロパティ ページ (プロジェクト)](/cpp/ide/general-property-page-project)
- [コンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)