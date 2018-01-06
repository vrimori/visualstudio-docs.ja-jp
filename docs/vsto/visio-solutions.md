---
title: "Visio ソリューション |Microsoft ドキュメント"
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
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 77c4b8e13071486bf483fc5b281bf86ae13aa965
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="visio-solutions"></a>Visio ソリューション
  Visual Studio には、Microsoft Office Visio の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Visio の自動化、Visio 機能の拡張、または Visio ユーザー インターフェイス (UI) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、「 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 」および「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。Microsoft Office でのプログラミングに慣れていない場合は、次を参照してください。[作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)です。  
  
 **対象:** このトピックの情報は、Visio 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、「 [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="automating-visio-by-using-the-visio-object-model"></a>Visio オブジェクト モデルによる Visio の自動化  
 Visio オブジェクト モデルでは、組織図、フローチャート、プロジェクト タイムライン、ネットワーク ダイアグラム、事務所スペースなどのダイアグラムを Visio で自動的に作成するために使用できる多数のクラスが公開されています。 この API を使用して、次のような一般的なタスクを実行するコードを作成できます。  
  
-   図形やテキストを作成し、ダイアグラムに配置する。  
  
-   ビジネス ロジックやユーザー入力に基づいて図形の動作を管理する。  
  
-   ダイアグラムの視覚エフェクト (パン、ズームなど) を制御する。  
  
-   アプリケーション UI をカスタマイズする。  
  
-   外部データを Visio にインポートし、図形にリンクしてページ上にグラフィカルに表示する。  
  
 Visio のオブジェクト モデルを使用して図面および図形を操作する手順やコード例については、「 [Working with Visio Documents](../vsto/working-with-visio-documents.md) 」および「 [Working with Visio Shapes](../vsto/working-with-visio-shapes.md)」を参照してください。  
  
 VSTO アドインから Visio オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application`フィールドは、Visio の現在のインスタンスを表す Microsoft.Office.Interop.Visio.Application オブジェクトを返します。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 Visio オブジェクト モデルを呼び出すときは、Visio のプライマリ相互運用機能アセンブリ (PIA) に用意された型を使用します。 PIA は、VSTO アドインのマネージ コードと Visio の COM オブジェクト モデルとの橋渡し役として機能します。 Visio PIA のすべての型で定義されます。 プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
## <a name="visio-object-model-overview"></a>Visio オブジェクト モデルの概要  
 Visio オブジェクト モデルの概要については、Visio オブジェクト モデルのリファレンスや SDK へのリンクを含む「 [Visio Object Model Overview](../vsto/visio-object-model-overview.md)」を参照してください。  
  
## <a name="customizing-the-user-interface-of-visio"></a>Visio のユーザー インターフェイスのカスタマイズ  
 Visio の UI には、次のようなカスタマイズ オプションがあります。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|リボンをカスタマイズします。|[リボンの概要](../vsto/ribbon-overview.md)|  
  
 Visio の UI をカスタマイズする方法の詳細については、 [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) クラスの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Office 開発における Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  