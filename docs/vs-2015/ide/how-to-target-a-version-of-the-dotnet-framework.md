---
title: '方法: .NET Framework のバージョンをターゲットにする | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3370c62535f2bb915115533ea79f4b913c3ac347
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182365"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>方法: .NET Framework のバージョンをターゲットにする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このドキュメントでは、プロジェクトを作成するときに特定のバージョンの .NET Framework を対象とする方法と、既存の Visual Basic、Visual C#、または Visual F# プロジェクトの中で対象のバージョンを変更する方法を説明します。  
  
> [!IMPORTANT]
>  C++ プロジェクトのターゲット バージョンを変更する方法については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)」を参照してください。  
  
 **このトピックの内容**  
  
-   [プロジェクト作成時にバージョンを対象として設定](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [ターゲット バージョンの変更](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> プロジェクト作成時にバージョンを対象として設定  
 プロジェクト作成時に対象として設定する .NET Framework のバージョンによって、使用できるテンプレートが決まります。  
  
> [!NOTE]
>  Visual Studio の Express Edition では、このトピックの「[ターゲット バージョンの変更](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)」で説明されているように、プロジェクトを作成した後でターゲットを変更できます。  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>プロジェクト作成時にバージョンを対象として設定するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの上部にある一覧で、プロジェクトの対象とする .NET Framework のバージョンを選択します。  
  
    > [!NOTE]
    >  通常、.NET Framework の 1 種類のバージョンのみが、Visual Studio と共にインストールされます。 別のバージョンを対象とする場合は、そのバージョンがインストールされていることを最初に確認する必要があります。 「[Visual Studio のマルチ ターゲットの概要](../ide/visual-studio-multi-targeting-overview.md)」を参照してください。  
  
3.  インストール済みテンプレートのリストで、作成しようとするプロジェクトの種類を選択し、プロジェクトに名前を付けて **[OK]** をクリックします。  
  
     テンプレートの一覧には、選択した .NET Framework のバージョンによってサポートされるプロジェクトのみが表示されます。  
  
##  <a name="bkmk_existing"></a> ターゲット バージョンの変更  
 次の手順で、Visual Basic、Visual C#、または Visual F# プロジェクトの対象とする .NET Framework バージョンを変更できます。  
  
#### <a name="to-change-the-targeted-version"></a>対象とするバージョンを変更するには  
  
1.  **ソリューション エクスプローラー**で、変更するプロジェクトのショートカット メニューを開き、**[プロパティ]** を選択します。  
  
     ![Visual Studio のソリューション エクスプローラーのプロパティ](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  C++ プロジェクトのターゲット バージョンを変更する方法については、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)」を参照してください。  
  
2.  プロパティ ウィンドウの左側の列で、**[アプリケーション]** タブを選択します。  
  
     ![Visual Studio のアプリのプロパティの [アプリケーション] タブ](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Windows ストア アプリを作成した後は、Windows または .NET Framework のターゲット バージョンを変更することはできません。  
  
3.  **[ターゲット フレームワーク]** 一覧で、目的のバージョンを選択します。  
  
4.  表示される検証ダイアログ ボックスで **[はい]** ボタンを選択します。  
  
     プロジェクトがアンロードされます。 プロジェクトを再読み込みすると、上で選択した .NET Framework のバージョンが対象になります。  
  
    > [!NOTE]
    >  対象とするバージョンとは別の .NET Framework のバージョンへの参照がコードに含まれている場合、コードをコンパイルまたは実行するとエラー メッセージが表示されることがあります。 これらのエラーを解決するには、参照を変更する必要があります。 「[.NET Framework を対象とするエラーのトラブルシューティング](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のマルチ ターゲットの概要](../ide/visual-studio-multi-targeting-overview.md)   
 [ASP.NET Web プロジェクト用の .NET Framework Multi-Targeting](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [.NET Framework を対象とするエラーのトラブルシューティング](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [プロジェクトの構成](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)



