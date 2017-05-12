---
title: "Visio ソリューション"
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
  - "Office プロジェクト [Visual Studio での Office 開発]、Visio"
  - "ソリューション [Visual Studio での Office 開発]、Visio"
  - "Visio [Visual Studio での Office 開発]"
  - "テンプレート [Visual Studio での Office 開発]、Visio"
  - "プロジェクト [Visual Studio での Office 開発]、Visio"
  - "Office ソリューション [Visual Studio での Office 開発]、Visio"
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Visio ソリューション
  Visual Studio には、Microsoft Office Visio の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Visio の自動化、Visio 機能の拡張、または Visio ユーザー インターフェイス \(UI\) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、「[VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)」および「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。 Microsoft Office でのプログラミングの経験がない場合は、「[はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)」を参照してください。  
  
 **対象:** このトピックの情報は、Visio 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
## Visio オブジェクト モデルによる Visio の自動化  
 Visio オブジェクト モデルでは、組織図、フローチャート、プロジェクト タイムライン、ネットワーク ダイアグラム、事務所スペースなどのダイアグラムを Visio で自動的に作成するために使用できる多数のクラスが公開されています。 この API を使用して、次のような一般的なタスクを実行するコードを作成できます。  
  
-   図形やテキストを作成し、ダイアグラムに配置する。  
  
-   ビジネス ロジックやユーザー入力に基づいて図形の動作を管理する。  
  
-   ダイアグラムの視覚エフェクト \(パン、ズームなど\) を制御する。  
  
-   アプリケーション UI をカスタマイズする。  
  
-   外部データを Visio にインポートし、図形にリンクしてページ上にグラフィカルに表示する。  
  
 Visio のオブジェクト モデルを使用して図面および図形を操作する手順やコード例については、「[Visio 図面の操作](../vsto/working-with-visio-documents.md)」および「[Visio の図形の操作](../vsto/working-with-visio-shapes.md)」を参照してください。  
  
 VSTO アドインから Visio オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。`Application` フィールドは、Visio の現在のインスタンスを表す Microsoft.Office.Interop.Visio.Application オブジェクトを返します。 詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
 Visio オブジェクト モデルを呼び出すときは、Visio のプライマリ相互運用機能アセンブリ \(PIA\) に用意された型を使用します。 PIA は、VSTO アドインのマネージ コードと Visio の COM オブジェクト モデルとの橋渡し役として機能します。 Visio PIA のすべての型は、Microsoft.Office.Interop.Visio 名前空間で定義されます。 プライマリ相互運用機能アセンブリの詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」および「[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。  
  
## Visio オブジェクト モデルの概要  
 Visio オブジェクト モデルの概要については、Visio オブジェクト モデルのリファレンスや SDK へのリンクを含む「[Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)」を参照してください。  
  
## Visio のユーザー インターフェイスのカスタマイズ  
 Visio の UI には、次のようなカスタマイズ オプションがあります。  
  
|タスク|詳細情報|  
|---------|----------|  
|リボンをカスタマイズします。|[リボンの概要](../vsto/ribbon-overview.md)|  
  
 Visio の UI をカスタマイズする方法の詳細については、[Visio.UIObject](HV10077129) クラスの VBA リファレンス ドキュメントを参照してください。  
  
## 参照  
 [VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Office 開発における Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  