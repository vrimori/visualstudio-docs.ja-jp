---
title: "PowerPoint ソリューション"
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
  - "Office ソリューション [Visual Studio での Office 開発]、PowerPoint"
  - "テンプレート [Visual Studio での Office 開発]、PowerPoint"
  - "ソリューション [Visual Studio での Office 開発]、PowerPoint"
  - "プロジェクト [Visual Studio での Office 開発]、PowerPoint"
  - "PowerPoint [Visual Studio での Office 開発]"
  - "Office プロジェクト [Visual Studio での Office 開発]、PowerPoint"
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# PowerPoint ソリューション
  Visual Studio には、Microsoft Office PowerPoint の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用すると、PowerPoint の自動化、PowerPoint 機能の拡張、PowerPoint ユーザー インターフェイス \(UI\) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、「[VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)」および「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。 Microsoft Office でのプログラミングの経験がない場合は、「[はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)」を参照してください。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.png "ビデオへのリンク")関連するビデオ デモについては、「[操作方法: Microsoft PowerPoint 用のアドインを作成する](http://go.microsoft.com/fwlink/?LinkId=132767)」を参照してください。  
  
## PowerPoint のオブジェクト モデルを使用した PowerPoint の自動化  
 PowerPoint オブジェクト モデルでは、PowerPoint の自動化に使用できる型が多数公開されています。 それらの型によって、次のような一般的なタスクを実行するコードを作成できます。  
  
-   プログラムによるプレゼンテーションの作成と書式指定  
  
-   プレゼンテーションへのスライドの追加または削除  
  
-   スライドへの図形の追加または変更  
  
 VSTO アドインから PowerPoint オブジェクト モデルにアクセスするには、プロジェクト内の `ThisAddIn` クラスの `Application` フィールドを使用します。`Application` フィールドは PowerPoint の現在のインスタンスを表す <xref:Microsoft.Office.Interop.PowerPoint.Application> オブジェクトを返します。 詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
 PowerPoint オブジェクト モデルを呼び出すときには、PowerPoint のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージ コードと PowerPoint の COM オブジェクト モデルとの仲介役を果たします。 PowerPoint プライマリ相互運用機能アセンブリ内の型は、すべて <xref:Microsoft.Office.Interop.PowerPoint> 名前空間に定義されています。 プライマリ相互運用機能アセンブリの詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」および「[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。  
  
##  <a name="WordOMDocumentation"></a> PowerPoint オブジェクト モデル ドキュメントの使用  
 PowerPoint オブジェクト モデルの詳細については、PowerPoint プライマリ相互運用機能アセンブリ \(PIA\) のリファレンスと、VBA オブジェクト モデルのリファレンスを参照してください。  
  
### プライマリ相互運用機能アセンブリのリファレンス  
 PowerPoint PIA のリファレンス ドキュメントは、PowerPoint のプライマリ相互運用機能アセンブリの型について説明しています。 このドキュメントは、「[PowerPoint 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189588)」から入手できます。  
  
 PIA のクラスとインターフェイスの違い、PIA のイベントの実装方法など、PowerPoint PIA の設計の詳細については、「[Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=199885)」を参照してください。  
  
### VBA オブジェクト モデルのリファレンス  
 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications \(VBA\) コードに公開される PowerPoint オブジェクト モデルについて説明しています。 詳細については、「[PowerPoint 2010 オブジェクト モデルのリファレンス](http://go.microsoft.com/fwlink/?LinkId=199770)」を参照してください。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、PowerPoint プライマリ相互運用機能アセンブリ \(PIA\) の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンス内の Presentation オブジェクトは、PowerPoint PIA の <xref:Microsoft.Office.Interop.PowerPoint.Presentation> 型に対応します。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した PowerPoint VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C\# に変換する必要があります。  
  
## PowerPoint のユーザー インターフェイスのカスタマイズ  
 PowerPoint の UI を次のように変更できます。  
  
|タスク|詳細情報|  
|---------|----------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
|リボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
|リボン上の組み込みタブにカスタム グループを追加する。|[方法 : 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 PowerPoint およびその他の Microsoft Office アプリケーションの UI をカスタマイズする方法の詳細については、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。  
  
## 参照  
 [チュートリアル : 初めての PowerPoint 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [VSTO アドインのプログラミングについて](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office 開発における PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  