---
title: Visual Studio で .NET Framework のターゲット バージョンを指定する
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6d0eef8a9563fdb6d74737f90cf184186142a672
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>方法: .NET Framework のターゲット バージョンを指定する

このドキュメントでは、プロジェクトを作成するときに特定のバージョンの .NET Framework を対象とする方法と、既存の Visual Basic、C#、または Visual F# プロジェクトの中で対象のバージョンを変更する方法を説明します。

> [!IMPORTANT]
> C++ プロジェクトのターゲット バージョンを変更する方法については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)」を参照してください。

## <a name="to-target-a-version-when-you-create-a-project"></a>プロジェクト作成時にバージョンを対象として設定するには

プロジェクトを作成したときに使用できる .NET Framework のバージョンは、インストールされているバージョンと **[新しいプロジェクト]** ダイアログ ボックスで選択したテンプレートによって変わります。

1. メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

1. インストールされているテンプレートの一覧で、作成するプロジェクトの種類を選択し、プロジェクトの名前を入力します。

1. **[新しいプロジェクト]** ダイアログ ボックスの下部にある **[Framework]** ドロップダウン リストから、プロジェクトでターゲットとする .NET Framework のバージョンを選択します。

    [Framework] リストには、選択したテンプレートに適用できるバージョンのみが表示されます。 .NET Core など、プロジェクトの種類によっては、.NET Framework が必要ありません。 このような場合、**[Framework]** ドロップダウン リストは非表示になります。

    ![[新しいプロジェクト] ダイアログ ボックスの [Framework] ドロップダウン リスト](media/vside-newproject-framework.png)

1. **[OK]** を選択します。

## <a name="to-change-the-targeted-version"></a>対象とするバージョンを変更するには

次の手順で、Visual Basic、C#、または Visual F# プロジェクトの対象とする .NET Framework バージョンを変更できます。

C++ プロジェクトのターゲット バージョンを変更する方法については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)」を参照してください。

1. **ソリューション エクスプローラー**で、変更するプロジェクトのショートカット メニューを開き、**[プロパティ]** を選択します。

    ![Visual Studio のソリューション エクスプローラーのプロパティ](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

1. **[プロパティ]** ウィンドウの左側の列で、**[アプリケーション]** タブを選択します。

    ![Visual Studio のアプリのプロパティの [アプリケーション] タブ](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > UWP アプリを作成した後は、Windows または .NET Framework のターゲット バージョンを変更することはできません。

1. **[ターゲット フレームワーク]** 一覧で、目的のバージョンを選択します。

1. 表示される検証ダイアログ ボックスで **[はい]** ボタンを選択します。

    プロジェクトがアンロードされます。 プロジェクトを再読み込みすると、上で選択した .NET Framework のバージョンが対象になります。

    > [!NOTE]
    > 対象とするバージョンとは別の .NET Framework のバージョンへの参照がコードに含まれている場合、コードをコンパイルまたは実行するとエラー メッセージが表示されることがあります。 これらのエラーを解決するには、参照を変更する必要があります。 「[.NET Framework を対象とするエラーのトラブルシューティング](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [Visual Studio のマルチ ターゲットの概要](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework を対象とするエラーのトラブルシューティング](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)