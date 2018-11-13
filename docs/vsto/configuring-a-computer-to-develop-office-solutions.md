---
title: Office ソリューションを開発コンピューターを構成します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19c7e012775ff1a761b5c267f05b8f7ff250d5c6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672227"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Office ソリューションを開発コンピューターを構成します。

Microsoft Office の VSTO アドインおよびカスタマイズを作成するには、Visual Studio、.NET Framework、Microsoft Office のサポートされているバージョンをインストールします。

|ソフトウェア|サポートされているバージョン|
|--------------|------------------------|
|Visual Studio 2017| 任意のエディションで、 **Office/sharepoint 開発**ワークロード。|
|.NET Framework|-.NET Framework 4 以降。|
|Microsoft Office|<ul><li>Office Professional Plus for Office 365 を含む Office のいずれかのスイート エディション。</li><li>次のいずれかのスタンドアロン アプリケーション:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 および Office 2010 のみ)</li><li>Outlook</li><li>PowerPoint</li><li>プロジェクト</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) は Office の一部としてインストールされている必要があります。 **重要:** クリックの実行のバージョンの Office 2010 のアプリケーションはサポートされていません。|

詳細なインストール手順については、次を参照してください。[方法: Office ソリューションを開発コンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)します。

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>プロジェクト テンプレートが表示されない、または Visual Studio では動作しません

Visual Studio、.NET Framework、および Microsoft Office のサポートされているバージョンをインストールする Office プロジェクト テンプレートは、Visual Studio で表示されないか場合**新しいプロジェクト**ダイアログ ボックスで、または、いずれかを使用しようとすると、エラーが発生次を確認します。

- 使用するコンピューターに Microsoft Office Developer Tools がインストールされていることを確認します。

     Office developer tools は、Visual Studio のオプションのコンポーネントが、Visual Studio と共に自動的にインストールされます。 インストールする機能を指定して Visual Studio のインストールをカスタマイズする場合は、各種ツールをインストールするために、セットアップ時に必ず **[Microsoft Office Developer Tools]** を選択してください。

     これらのツールがインストールされていることを確認する、Visual Studio のセットアップ プログラムを開始して、**変更**ボタンをクリックします。 **[Microsoft Office Developer Tools]** チェック ボックスをオンにして **[更新]** ボタンをクリックします。

- 実行で提供された Office のバージョンを実行していないことを確認します。 参照してください[方法: Outlook がコンピューター上のクリック クイック実行アプリケーションかどうかを確認](/previous-versions/office/developer/office-2010/ff864733(v=office.14))します。

- Microsoft Office の 1 つだけのバージョンを実行していることを確認します。

問題が発生する場合を参照してください。 [Office ソリューションのエラーのための追加サポート](../vsto/additional-support-for-errors-in-office-solutions.md)します。

## <a name="see-also"></a>関連項目

[開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[方法: Office ソリューションを開発コンピューターを構成します。](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[方法: Visual Studio Tools for Office ランタイム再頒布可能パッケージのインストール](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[方法: Office プライマリ相互運用機能アセンブリ](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Office アプリケーションおよびプロジェクトの種類で使用できる機能](../vsto/features-available-by-office-application-and-project-type.md)
