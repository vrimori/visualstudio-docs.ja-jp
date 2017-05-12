---
title: "Project ソリューション"
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
  - "プロジェクト [Visual Studio での Office 開発]、プロジェクト"
  - "Office ソリューション [Visual Studio での Office 開発]、プロジェクト"
  - "Project [Visual Studio での Office 開発]"
  - "テンプレート [Visual Studio での Office 開発]、プロジェクト"
  - "Office プロジェクト [Visual Studio での Office 開発]、プロジェクト"
  - "ソリューション [Visual Studio での Office 開発]、プロジェクト"
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Project ソリューション
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] には、Microsoft Office Project の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用すると、Project の自動化、Project 機能の拡張、Project ユーザー インターフェイス \(UI\) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、「[VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)」および「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。 Microsoft Office でのプログラミングの経験がない場合は、「[はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)」を参照してください。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
## Project オブジェクト モデルによる Project の自動化  
 Project オブジェクト モデルでは、Project の自動化に使用できる型が多数公開されています。 これらの型により、プロジェクト内のタスクをプログラムによって作成したり変更したりするなど、一般的なタスクを行うコードを記述できます。  
  
 VSTO アドインから Project オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。`Application` フィールドは Project の現在のインスタンスを表す Microsoft.Office.Interop.MsProject.Application  オブジェクトを返します。 詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
 Project オブジェクト モデルを呼び出すときには、Project のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージ コードと Project の COM オブジェクト モデルとの仲介役を果たします。 Project プライマリ相互運用機能アセンブリ内の型は、すべて Microsoft.Office.Interop.MSProject 名前空間に定義されています。 プライマリ相互運用機能アセンブリの詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」および「[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。  
  
## Project オブジェクト モデル ドキュメントの使用  
 Project オブジェクト モデルの詳細については、Project の VBA オブジェクト モデルのリファレンスを参照してください。 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications \(VBA\) コードに公開される Project オブジェクト モデルについて説明しています。 詳細については、「[Project 2010 オブジェクト モデルのリファレンス](http://go.microsoft.com/fwlink/?LinkId=199771)」を参照してください。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Project プライマリ相互運用機能アセンブリ \(PIA\) の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンス内の Calendar オブジェクトは、Project PIA の Microsoft.Office.Interop.MSProject.Calendar 型に対応します。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した Project VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C\# に変換する必要があります。  
  
> [!NOTE]  
>  現在のところ、Project プライマリ相互運用機能アセンブリに関するリファレンス ドキュメントは提供されていません。  
  
### Project プライマリ相互運用機能アセンブリのインフラストラクチャの型  
 Project PIA を使用するコードを作成すると、VBA リファレンスには記載されていない型が多数あることに気付きます。 そうした追加の型は、Project の COM ベースのオブジェクト モデルに含まれるオブジェクトをマネージ コードに変換する場合に役立ちますが、コード内で直接使用することを目的としたものではありません。  
  
 詳細については、「[Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)」を参照してください。  
  
## Project のユーザー インターフェイスのカスタマイズ  
 Project の UI は次の方法でカスタマイズできます。  
  
|タスク|詳細情報|  
|---------|----------|  
|Project のリボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
  
 Project およびその他の Microsoft Office アプリケーションの UI をカスタマイズする方法の詳細については、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。  
  
## 参照  
 [チュートリアル: 初めての Project 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office 開発における Project 2010 と Project Server 2010](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  