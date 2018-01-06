---
title: "Office UI のカスタマイズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
ms.assetid: 3d7c7b88-2053-4ada-bfe7-e7bb202c430b
caps.latest.revision: "74"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c169edc949f195d416194ae3c3ee1111977f649b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="office-ui-customization"></a>Office UI のカスタマイズ
  Microsoft Office アプリケーションのユーザー インターフェイス (UI) は、Visual Studio の  Office Developer Tools を使用してカスタマイズできます。 以下のトピックでは、カスタマイズできる UI 機能について説明します。  
  
-   [UI の機能の比較](#Comparison)  
  
-   [操作ウィンドウやカスタム作業ウィンドウ](#Actions)  
  
-   [カスタム リボン UI](#Ribbon)  
  
-   [Backstage ビュー](#Backstage)  
  
-   [Outlook フォーム領域](#FormRegion)  
  
-   [ドキュメントのコントロール](#Controls)  
  
-   [ショートカット メニュー](#Shortcut)  
  
##  <a name="Comparison"></a>UI の機能の比較  
 次の表では、Microsoft Office プロジェクトでカスタマイズできる主な UI 機能を比較します。  
  
|機能|サポートされているプロジェクトの種類|サポートされる Microsoft Office アプリケーション|  
|-------------|-----------------------------|---------------------------------------------|  
|[操作] ウィンドウ|ドキュメント レベルのカスタマイズ|Excel<br /><br /> Word|  
|カスタム作業ウィンドウ|VSTO アドイン|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|カスタム リボンの UI|ドキュメント レベルのカスタマイズ<br /><br /> VSTO アドイン|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> プロジェクト<br /><br /> Word<br /><br /> Visio|  
|Backstage ビュー|ドキュメント レベルのカスタマイズ<br /><br /> VSTO アドイン|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]。<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> プロジェクト<br /><br /> Word<br /><br /> Visio|  
|Outlook フォーム領域|VSTO アドイン|Outlook|  
|ドキュメントのコントロール|ドキュメント レベルのカスタマイズ<br /><br /> VSTO アドイン|Excel<br /><br /> Word|  
|ショートカット メニュー|ドキュメント レベルのカスタマイズ<br /><br /> VSTO アドイン|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> プロジェクト<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a>操作ウィンドウやカスタム作業ウィンドウ  
 作業ウィンドウは、通常、Microsoft Office アプリケーションのウィンドウの一辺にドッキングされているユーザー インターフェイス ウィンドウです。 ほぼすべての Microsoft Office アプリケーションには組み込みの作業ウィンドウがあります。 作業ウィンドウの例として、Word のヘルプ作業ウィンドウがあります。  
  
 Visual Studio の Office 開発ツールには、作業ウィンドウをカスタマイズする方法が 2 つあります。  
  
-   ドキュメントレベルのカスタマイズには、操作ウィンドウを追加できます。 既定では、アプリケーションの右側、ドキュメントの右側に操作ウィンドウが表示されます。 操作ウィンドウは、ドキュメントの左、上、または下に表示することもできます。  
  
-   VSTO アドインには、カスタム作業ウィンドウを追加できます。 ユーザーは、アプリケーション ウィンドウのいずれかの辺にカスタム作業ウィンドウをドッキングすることができます。また、ウィンドウの任意の場所にカスタム作業ウィンドウをドラッグすることができます。  
  
 操作ウィンドウやカスタム作業ウィンドウには、データ エントリなど、ユーザーの作業を支援するさまざまなコントロールが用意されています。 リボン グループと比較すると、操作ウィンドウとカスタム作業ウィンドウには、テキストやコントロールを含む大きな領域があります。  
  
 操作ウィンドウの詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)です。 カスタム作業ウィンドウの詳細については、次を参照してください。[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)します。  
  
##  <a name="Ribbon"></a>カスタム リボン UI  
 Office のアプリケーションに追加する機能を表示するようにリボン UI をカスタマイズすることができます。 リボンを使用すると、関連するコマンドを (コントロールの形式で) 見つけやすいように整理できます。 独自のリボン タブとグループを作成し、ソリューションで提供する機能にユーザーがアクセスできるようにすることができます。 旧バージョンの Microsoft Office System でメニューとツールバーを使用してアクセスしていた機能の多くは、現在ではリボンを使用してアクセスできます。  
  
 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
##  <a name="Backstage"></a>Backstage ビュー  
 Office アプリケーションをクリックすると、**ファイル**タブには、Backstage ビューが表示されます。 Backstage ビューには、ファイルレベルのタスクと操作を組み合わせた UI が用意されています。Backstage は、2007 Microsoft Office System の Microsoft Office ボタンで使用できる似た機能の置き換えです。 Backstage ビューは、XML を使用してフルに拡張することができます。  
  
 Visual Studio には、Backstage ビューをカスタマイズできるデザイナーや API が用意されていません。 ただし、追加する場合、**リボン (XML)**項目、Office プロジェクトには、Backstage ビューをカスタマイズするリボン XML ファイルに XML を追加できます。 詳細については**リボン (XML)** 、項目を参照してください[リボン XML](../vsto/ribbon-xml.md)です。  
  
 Backstage ビューのカスタマイズの詳細については、次を参照してください。[開発者向けの Office 2010 の Backstage ビューの概要](http://go.microsoft.com/fwlink/?LinkId=182189)と[開発者向けの Office 2010 の Backstage ビューをカスタマイズする](http://go.microsoft.com/fwlink/?LinkId=182188)です。  
  
##  <a name="FormRegion"></a>Outlook フォーム領域  
 標準の Microsoft Office Outlook フォームにカスタム機能を追加するには、フォーム領域を使用します。 フィールドまたはコントロールを追加して既存のフォームを拡張するフォーム領域を作成できます。 Visual Studio で Office 開発ツールを使用して新しいフォーム領域を作成する場合、フォーム領域には Windows フォーム コントロールのみを使用できます。 Outlook で設計したフォーム領域をインポートする場合、ネイティブ Outlook コントロールのみを使用できます。  
  
 Outlook UI のさまざまな領域を占有するフォーム領域を作成できます。 たとえば、隣接するフォーム領域をフォームの最初のページの下部に表示し、隣接する各フォーム領域を展開可能にすることができます。 また、完全な追加のフォーム ページとして表示し、既存の標準フォームまたはカスタム フォームに表示できる個別のフォーム領域を追加することもできます。  
  
 詳細については、「 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)」を参照してください。  
  
##  <a name="Controls"></a>ドキュメントのコントロール  
 Word 文書と Excel ワークシートには多様なコントロールを追加できます。 たとえば、日付選択カレンダー コントロールを文書に追加して、ユーザーが標準の形式で日付を入力できるようにしたり、データベースにデータを送信するボタンをワークシートに追加したりすることができます。  
  
 Excel または Word のドキュメントレベル プロジェクトを開発する場合、Visual Studio デザイナーを使用し、設計時にプロジェクトの文書またはブックにコントロールを追加できます。また、実行時にプログラムで追加することもできます。 Excel または Word の VSTO アドイン プロジェクトを開発するとき、実行時に開いているドキュメントやブックにこれらのコントロールをプログラミングで追加できます。  
  
 詳細については、 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) および [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)を参照してください。  
  
##  <a name="Shortcut"></a>ショートカット メニュー  
 ドキュメント ウィンドウやアプリケーション ウィンドウを右クリックすると、ショートカット メニューが表示されます。 ユーザーがドキュメント、ブック、またはホスト コントロールを右クリックするなど、イベントが発生した後に表示されるようにショートカット メニューを設定することができます。 ショートカット メニューには、さまざまなメニュー コマンドやコントロールを追加できます。 ショートカット メニューを作成するには、XML を使用します。 追加する場合、**リボン (XML)**項目、Office プロジェクトにショートカット メニューを作成、リボン XML ファイルに XML を追加することができます。 XML を使用して、ショートカット メニューを作成する方法の詳細については、次を参照してください。[する方法: ショートカット メニューにコマンドを追加](../vsto/how-to-add-commands-to-shortcut-menus.md)です。  
  
## <a name="see-also"></a>参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [Windows フォームでコントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [カスタム作業ウィンドウ](../vsto/custom-task-panes.md)   
 [Office ソリューションで WPF コントロールの使用](../vsto/using-wpf-controls-in-office-solutions.md)   
 [方法: リボンに [開発] タブを表示](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [方法: アドイン ユーザー インターフェイス エラーを表示します。](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [チュートリアル: Windows フォームを使用してデータを収集する方法](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  