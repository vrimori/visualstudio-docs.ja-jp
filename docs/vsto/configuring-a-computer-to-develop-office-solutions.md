---
title: "Office ソリューションを開発できるようにコンピューターを構成する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での Office 開発、インストール (ツールの)"
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: 97
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Office ソリューションを開発できるようにコンピューターを構成する
  Microsoft Office の VSTO アドインおよびカスタマイズを作成するには、Visual Studio、.NET Framework、Microsoft Office のサポートされているバージョンをインストールします。  
  
|ソフトウェア|サポートされているバージョン|  
|------------|--------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)] **Important:**  セットアップのときに、\[Microsoft Office Developer Tools\] チェック ボックスをオンにしておく必要があります。|  
|.NET Framework|-   .NET Framework 4 以降|  
|Microsoft Office|<ul><li>Office Professional Plus for Office 365 を含む Office のいずれかのスイート エディション。</li><li>次のいずれかのスタンドアロン アプリケーション:<br /><br /> <ul><li>Excel</li><li>InfoPath \(Office 2013 および Office 2010 のみ\)</li><li>Outlook</li><li>PowerPoint</li><li>プロジェクト</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications \(VBA\) は Office の一部としてインストールされている必要があります。 **Important:**  Office 2010 アプリケーションのクイック実行バージョンはサポートされていません。|  
  
 インストール手順について詳しくは、「[方法: Office ソリューションを開発できるようにコンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)」をご覧ください。  
  
## プロジェクト テンプレートが表示されない、または Visual Studio でプロジェクト テンプレートが機能しない場合  
 Visual Studio、.NET Framework、および Microsoft Office のサポートされているバージョンをインストールしても、Visual Studio の **\[新しいプロジェクト\]** ダイアログ ボックスに Office のプロジェクト テンプレートが表示されない、またはプロジェクト テンプレートの使用を試みるとエラーが表示される場合は、以下のことを確認してください。  
  
-   使用するコンピューターに Microsoft Office Developer Tools がインストールされていることを確認します。  
  
     Office Developer Tools は Visual Studio のオプション コンポーネントですが、通常は Visual Studio とともに自動的にインストールされます。 インストールする機能を指定して Visual Studio のインストールをカスタマイズする場合は、各種ツールをインストールするために、セットアップ時に必ず **\[Microsoft Office Developer Tools\]** を選択してください。  
  
     これらのツールがインストールされていることを確認するには、Visual Studio のセットアップ プログラムを開始して **\[変更\]** ボタンをクリックします。**\[Microsoft Office Developer Tools\]** チェック ボックスをオンにして **\[更新\]** ボタンをクリックします。  
  
-   クイック実行で提供された、Office のバージョンを実行していないことを確認します。 「[方法: コンピューター上の Outlook がクイック実行アプリケーションかどうかを検証する](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx)」をご覧ください。  
  
-   Microsoft Office の 1 つのバージョンのみを実行していることを確認します。  
  
 問題が解決しない場合は、「[Office ソリューションのエラーについての追加サポート](../vsto/additional-support-for-errors-in-office-solutions.md)」をご覧ください。  
  
## 参照  
 [はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [方法: Office ソリューションを開発できるようにコンピューターを構成する](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [方法: Visual Studio Tools for Office の再頒布可能なランタイムをインストールする](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [方法 : Office のプライマリ相互運用機能アセンブリをインストールする](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)  
  
  