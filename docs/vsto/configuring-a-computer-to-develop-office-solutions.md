---
title: "Office ソリューションを開発コンピューターを構成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 9b63b3b495b9cb15ea3e9eeedcecedb3a384f8a0
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Office ソリューションを開発できるようにコンピューターを構成する

Microsoft Office の VSTO アドインおよびカスタマイズを作成するには、Visual Studio、.NET Framework、Microsoft Office のサポートされているバージョンをインストールします。

|ソフトウェア|サポートされているバージョン|
|--------------|------------------------|
|Visual Studio 2017| 任意のエディションで、 **Office/sharepoint 開発**ワークロード。|
|.NET Framework|-.NET Framework 4 以降。|
|Microsoft Office|<ul><li>Office Professional Plus for Office 365 を含む Office のいずれかのスイート エディション。</li><li>次のいずれかのスタンドアロン アプリケーション:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 および Office 2010 のみ)</li><li>Outlook</li><li>PowerPoint</li><li>プロジェクト</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) は Office の一部としてインストールされている必要があります。 **重要:** Office 2010 アプリケーションのバージョンを実行するためのクリックがサポートされていません。|

詳細なインストール手順については、次を参照してください。[する方法: Office ソリューションの開発にコンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)です。

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>プロジェクト テンプレートが表示されない、または Visual Studio では動作しません

Visual Studio、.NET Framework および Microsoft Office のサポートされているバージョンをインストールするか、Office プロジェクト テンプレートが Visual Studio で表示されない場合**新しいプロジェクト**ダイアログ ボックスで、または、1 つを使用しようとすると、エラーが発生次を確認します。

- 使用するコンピューターに Microsoft Office Developer Tools がインストールされていることを確認します。

     Office Developer Tools は Visual Studio のオプション コンポーネントですが、通常は Visual Studio とともに自動的にインストールされます。 インストールする機能を指定して Visual Studio のインストールをカスタマイズする場合は、各種ツールをインストールするために、セットアップ時に必ず **[Microsoft Office Developer Tools]** を選択してください。

     これらのツールがインストールされていることを確認する、Visual Studio のセットアップ プログラムを開始し、選択、**変更**ボタンをクリックします。 **[Microsoft Office Developer Tools]** チェック ボックスをオンにして **[更新]** ボタンをクリックします。

- 実行するためのクリックで提供された、Office のバージョンを実行していないことを確認します。 「 [方法: コンピューター上の Outlook がクイック実行アプリケーションかどうかを検証する](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx)」をご覧ください。

- Microsoft Office のバージョンを 1 つだけを実行していることを確認します。

問題が解決しない場合は、「 [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md)」をご覧ください。

## <a name="see-also"></a>参照

[作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)  
[方法: Office ソリューションを開発できるようにコンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[方法: Visual Studio Tools for Office の再頒布可能なランタイムをインストールする](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[方法: Office のプライマリ相互運用機能アセンブリをインストールする](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)
