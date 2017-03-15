---
title: "Visual Studio の各バージョンで使用可能な機能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, 使用可能な機能"
ms.assetid: cb2728da-7705-4dea-a1c3-12a0388cb652
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio の各バージョンで使用可能な機能
次の表に、特定の機能が Visual Studio Professional の各バージョンでサポートされているかどうかを示します。  
  
-   「○」は、Visual Studio の当該バージョンにその機能が用意されていることを意味します。  
  
-   「追加」は、Visual Studio の当該バージョンにその機能は用意されていませんが、使用は可能であることを意味します。リンクをクリックすると、詳細な情報を確認できます。  
  
-   「×」は、Visual Studio の当該バージョンにその機能が用意されていないことを意味します。  
  
||Visual Studio 2010<br /><br /> および<br /><br /> Visual Studio 2010 SP1|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
|-|-----------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
|サポートされる .NET Framework のバージョン|2.0、3.0、3.5 SP1、4|2.0、3.0、3.5 SP1、4、4.5|2.0、3.0、3.5 SP1、4、4.5、4.5.1|  
|ローカル Web サーバー|○|はい|○|  
|SQL Server Express|2008|2008|2008|  
|サーバー エクスプローラーからの SQL Server の各バージョンへの接続|2000, 2005, 2008|2000, 2005, 2008|2000, 2005, 2008|  
|ASP.NET AJAX <sup>1</sup>|○|はい|○|  
|ASP.NET モデル ビュー コントローラー|○|はい|○|  
|ASP.NET 動的データ|○|はい|○|  
|MSBuild|○|はい|○|  
|ADO.NET Entity Framework|○|はい|○|  
|ADO.NET Data Services|○|はい|○|  
|Microsoft Azure Tools|追加|追加||  
|Smart Devices|Ｘ|Ｘ||  
|並列コンピューティング|○<sup>2</sup>|○|○|  
|Windows Communication Foundation|○|はい|○|  
|Windows Presentation Foundation|○|はい|○|  
|.NET Rich Internet Application サービス|[追加](http://go.microsoft.com/fwlink/?LinkID=230768)|○|○|  
|Silverlight 1|○|はい|○|  
|Silverlight 2|Ｘ|はい|○|  
|Silverlight 3|○|はい|○|  
|Silverlight 4|[追加](http://go.microsoft.com/fwlink/?LinkID=153710)|○|○|  
|Silverlight 5|[追加](http://go.microsoft.com/fwlink/?LinkID=215392), SP1 only.|○|○|  
|IronPython|[追加](http://go.microsoft.com/fwlink/?LinkID=183863)|[追加](http://go.microsoft.com/fwlink/?LinkID=183863)|[追加](http://go.microsoft.com/fwlink/?LinkID=183863)|  
|IronRuby|[追加](http://go.microsoft.com/fwlink/?LinkID=183864)|[追加](http://go.microsoft.com/fwlink/?LinkID=183864)|[追加](http://go.microsoft.com/fwlink/?LinkID=183864)|  
|Visual Studio Tools for Office|○<sup>4</sup><br /><br /> \(Office 2007、Office 2010\)|○<sup>4</sup>\(Office 2010\)|○<sup>4</sup>\(Office 2013\)|  
|レポート プロジェクト|○|はい|○|  
|レポート ウィザード|○|はい|○|  
|統合言語クエリ \(LINQ: Language\-Integrated Query\)|○|はい|○|  
|SharePoint 開発|○ \(SharePoint 2010 が対象\)|○ \(SharePoint 2010 が対象\)|○ \(SharePoint 2013 が対象\)|  
|.NET Framework 4 Client Profile のサポート|○|いいえ|Ｘ|  
  
1.  ASP.NET AJAX:  
  
     サーバー側: コントロールは ASP.NET 3.5 に含まれており、Visual Studio の**ツールボックス**に用意されています。  旧バージョンの ASP.NET、たとえば ASP.NET 2.0 を使用している場合は、[ASP.NET AJAX Extensions \(ASP.NET AJAX 拡張機能\)](http://go.microsoft.com/fwlink/?LinkID=75360) をダウンロードできます。  
  
     クライアント側: クライアント側の ASP.NET AJAX Library は ASP.NET 3.5 SP1 に含まれています。  
  
2.  並列コンピューティング:  
  
     並列拡張機能には、タスク並列ライブラリ \(TPL\)、並列 LINQ \(PLINQ\)、および同時実行データ構造があります。これらのコンポーネントは、.NET Framework 4 に含まれています。  ネイティブな C\+\+ 開発用の同等のライブラリとして、同時実行ランタイムとエージェント ライブラリがあります。これらのライブラリは、Visual Studio 2010 に組み込まれています。  プロファイラーおよびデバッガーの拡張機能も Visual Studio 2010 に組み込まれています。  
  
3.  IronPython および IronRuby:  
  
     IronPython および IronRuby の CodePlex Web サイトでは、いくつかのバージョンを入手できます。  使用する環境に適用するバージョンを選択します。  どちらの言語も最小要件は、.NET Framework 2.0 SP1 です。  
  
4.  Visual Studio Tools for Office \(VSTO\) の互換性およびアドイン機能:  
  
    ||Visual Studio 2010|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
    |-|------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
    |ドキュメント レベル|Word 2007、Word 2010、Excel 2007、Excel 2010|Word 2010、Excel 2010|Word 2013、Excel 2013|  
    |アプリケーション レベル|Word 2007、Word 2010、Excel 2007、Excel 2010、InfoPath 2007、InfoPath 2010、Outlook 2007、Outlook 2010、PowerPoint 2007、PowerPoint 2010、Visio 2007、Visio 2010、Project 2007、Project 2010|Word 2010、Excel 2010、InfoPath 2010、Outlook 2010、PowerPoint 2010、Visio 2010、Project 2010|Word 2013、Excel 2013、InfoPath 2013、Outlook 2013、PowerPoint 2013、Visio 2013、Project 2013|