---
title: "InfoPath ソリューション"
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
  - "ソリューション [Visual Studio での Office 開発]、InfoPath"
  - "テンプレート [Visual Studio での Office 開発]、InfoPath"
  - "InfoPath [Visual Studio での Office 開発]"
  - "Visual Studio での Office 開発、InfoPath ソリューション"
  - "プロジェクト [Visual Studio での Office 開発]、InfoPath"
  - "Office ソリューション [Visual Studio での Office 開発]、InfoPath"
  - "Office プロジェクト [Visual Studio での Office 開発]、InfoPath"
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# InfoPath ソリューション
  Visual Studio には、Microsoft Office InfoPath 2013 および InfoPath 2010 の VSTO アドインの作成に使用できるプロジェクト テンプレートが用意されています。 InfoPath は、Office 2016 では使用できません。  
  
> [!NOTE]  
>  Office 2016 をインストールしてある場合でも、InfoPath 用の VSTO アドインを作成することはできます。 InfoPath 2013 または Office 2013 を Office 2016 とサイドバイサイドにインストールするだけです。  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
 InfoPath 用の VSTO アドインは、他の Microsoft Office アプリケーションの VSTO アドインと似ています。 このようなソリューションは、アプリケーションが読み込むアセンブリで構成されます。 エンド ユーザーは、どのフォームまたはフォーム テンプレートが開いているかに関係なく、このアセンブリの機能にアクセスできます。 VSTO アドインについて詳しくは、「[VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)」および「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」をご覧ください。  
  
> [!NOTE]  
>  Visual Studio 2015 には、以前のバージョンの Visual Studio で提供されていた InfoPath フォーム テンプレート プロジェクトは含まれていません。 また、Visual Studio 2015 を使用して、以前のバージョンの Visual Studio で作成した InfoPath フォーム テンプレート プロジェクトを開いて編集することもできません。 ただし、Visual Studio Tools for Applications を使用すると、InfoPath フォーム テンプレート プロジェクトを開いて編集できます。 詳しくは、「[InfoPath 2010 での VSTO 2008 プロジェクトの使用](http://go.microsoft.com/fwlink/?LinkID=218903)」をご覧ください。  
  
## アドイン使用による InfoPath の自動化  
 Visual Studio の Office 開発ツールを使用して作成した Office VSTO アドインから InfoPath オブジェクト モデルにアクセスするには、プロジェクトの `ThisAddIn` クラスの `Application` フィールドを使用します。`Application` フィールドは InfoPath の現在のインスタンスを表す <xref:Microsoft.Office.Interop.InfoPath.Application> オブジェクトを返します。 詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
 VSTO アドインから InfoPath オブジェクト モデルを呼び出すときには、InfoPath のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージ コードと InfoPath の COM オブジェクト モデルとの仲介役を果たします。 InfoPath プライマリ相互運用機能アセンブリ内の型は、すべて <xref:Microsoft.Office.Interop.InfoPath> 名前空間に定義されています。 InfoPath プライマリ相互運用機能アセンブリの詳細については、「[Microsoft Office InfoPath プライマリ相互運用機能アセンブリについて](http://msdn.microsoft.com/ja-jp/1b3ae03c-6951-49e4-a489-4712d3f7ba72)」を参照してください。 プライマリ相互運用機能アセンブリ全般について詳しくは、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」および「[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」をご覧ください。  
  
## アドインによる InfoPath のユーザー インターフェイスのカスタマイズ  
 InfoPath の VSTO アドインを作成するときには、さまざまな方法で UI をカスタマイズできます。 次の表は、主なカスタマイズ方法を示しています。  
  
|タスク|詳細情報|  
|---------|----------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
|InfoPath のリボンにカスタム タブを追加する。|[InfoPath のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 InfoPath およびその他の Microsoft Office アプリケーションの UI をカスタマイズする方法について詳しくは、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」をご覧ください。  
  
## 参照  
 [Microsoft Office InfoPath のプライマリ相互運用機能アセンブリについて](http://msdn.microsoft.com/ja-jp/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office 開発における InfoPath 2010](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  