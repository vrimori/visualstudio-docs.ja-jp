---
title: '方法 : アプリケーション アイコンを指定する (Visual Basic、C#)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8da1de87031db962ede178a742325d9206e808c3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>方法 : アプリケーション アイコンを指定する (Visual Basic、C#)

プロジェクトの `Icon` プロパティでは、**ファイル エクスプローラー**と Windows タスク バーに表示されるコンパイルされたアプリケーションのアイコン ファイル (*.ico*) を指定します。

`Icon` プロパティには、**プロジェクト デザイナー**の **[アプリケーション]** ウィンドウからアクセスできます。このプロパティには、リソースまたはコンテンツ ファイルとしてプロジェクトに追加されているアイコンの一覧が含まれています。

> [!NOTE]
> アプリケーションのアイコン プロパティを設定した後、アプリケーション内の各 **Window** または **Form** の `Icon` プロパティを設定することもできます。 Windows Presentation Foundation (WPF) スタンドアロン アプリケーションのウィンドウ アイコンの詳細については、<xref:System.Windows.Window.Icon%2A> プロパティを参照してください。

## <a name="to-specify-an-application-icon"></a>アプリケーション アイコンを指定するには

1. **ソリューション エクスプローラー**で、**[ソリューション]** ノードではなくプロジェクト ノードを選びます。

1. メニュー バーで、**[プロジェクト]**  >  **[プロパティ]** を選択します。

1. **プロジェクト デザイナー**が表示されたら、**[アプリケーション]** タブを選びます。

1. **(Visual Basic)**&mdash; **[アイコン]** 一覧で、アイコン (*.ico*) ファイルを選びます。

    **(C#)**&mdash; **[アイコン]** 一覧の近くにある **\<参照>** ボタンを選び、目的のアイコン ファイルの場所を参照します。

## <a name="see-also"></a>関連項目

- [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)