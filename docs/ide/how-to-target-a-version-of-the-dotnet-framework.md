---
title: "方法: .NET Framework のバージョンをターゲットにする | Microsoft Docs"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: da2e236c39cce72670a47212aedabb87afa4d217
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>方法: .NET Framework のバージョンをターゲットにする

このドキュメントでは、プロジェクトを作成するときに特定のバージョンの .NET Framework を対象とする方法と、既存の Visual Basic、C#、または Visual F# プロジェクトの中で対象のバージョンを変更する方法を説明します。

> [!IMPORTANT]
> C++ プロジェクトのターゲット バージョンを変更する方法については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)」を参照してください。

## <a name="targeting-a-version-when-you-create-a-project"></a>プロジェクト作成時にバージョンを対象として設定

プロジェクト作成時に対象として設定する .NET Framework のバージョンによって、使用できるテンプレートが決まります。

### <a name="to-target-a-version-when-you-create-a-project"></a>プロジェクト作成時にバージョンを対象として設定するには

1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。

2.  **[新しいプロジェクト]** ダイアログ ボックスの上部にある一覧で、プロジェクトの対象とする .NET Framework のバージョンを選択します。

3.  インストール済みテンプレートのリストで、作成しようとするプロジェクトの種類を選択し、プロジェクトに名前を付けて **[OK]** をクリックします。

    テンプレートの一覧には、選択した .NET Framework のバージョンによってサポートされるプロジェクトのみが表示されます。

## <a name="changing-the-target-version"></a>ターゲット バージョンの変更

次の手順で、Visual Basic、C#、または Visual F# プロジェクトの対象とする .NET Framework バージョンを変更できます。

C++ プロジェクトのターゲット バージョンを変更する方法については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)」を参照してください。

### <a name="to-change-the-targeted-version"></a>対象とするバージョンを変更するには

1.  **ソリューション エクスプローラー**で、変更するプロジェクトのショートカット メニューを開き、**[プロパティ]** を選択します。

    ![Visual Studio のソリューション エクスプローラーのプロパティ](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

2. プロパティ ウィンドウの左側の列で、**[アプリケーション]** タブを選択します。

    ![Visual Studio のアプリのプロパティの [アプリケーション] タブ](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > UWP アプリを作成した後は、Windows または .NET Framework のターゲット バージョンを変更することはできません。

3.  **[ターゲット フレームワーク]** 一覧で、目的のバージョンを選択します。

4.  表示される検証ダイアログ ボックスで **[はい]** ボタンを選択します。

    プロジェクトがアンロードされます。 プロジェクトを再読み込みすると、上で選択した .NET Framework のバージョンが対象になります。

    > [!NOTE]
    > 対象とするバージョンとは別の .NET Framework のバージョンへの参照がコードに含まれている場合、コードをコンパイルまたは実行するとエラー メッセージが表示されることがあります。 これらのエラーを解決するには、参照を変更する必要があります。 「[.NET Framework を対象とするエラーのトラブルシューティング](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)」を参照してください。

## <a name="see-also"></a>関連項目

[Visual Studio のマルチ ターゲットの概要](../ide/visual-studio-multi-targeting-overview.md)  
[.NET Framework を対象とするエラーのトラブルシューティング](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)  
[[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)  
[[アプリケーション] ページ (プロジェクト デザイナー)](../ide/reference/application-page-project-designer-visual-basic.md)  
[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)