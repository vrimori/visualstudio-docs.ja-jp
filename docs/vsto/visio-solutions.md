---
title: Visio ソリューション
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7fc3f699cd33f2bb45487ca1329d812cfbeb950
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671548"
---
# <a name="visio-solutions"></a>Visio ソリューション
  Visual Studio には、Microsoft Office Visio の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Visio の自動化、Visio 機能の拡張、または Visio ユーザー インターフェイス (UI) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、次を参照してください。 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)と[Architecture of VSTO アドイン](../vsto/architecture-of-vsto-add-ins.md)します。Microsoft Office を使用したプログラミングに慣れていない場合は、次を参照してください。[開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)します。  
  
 **対象:** このトピックの情報は、Visio 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクトの種類別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
> [!NOTE]  
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、HTML5、JavaScript、CSS3、XML などのほぼすべての web プログラミング テクノロジを使用して、ビルドすることができます。  
  
## <a name="automate-visio-by-using-the-visio-object-model"></a>Visio オブジェクト モデルを使用して、Visio を自動化します。  
 Visio オブジェクト モデルでは、組織図、フローチャート、プロジェクト タイムライン、ネットワーク ダイアグラム、事務所スペースなどのダイアグラムを Visio で自動的に作成するために使用できる多数のクラスが公開されています。 この API を使用して、次のような一般的なタスクを実行するコードを作成できます。  
  
- 図形やテキストを作成し、ダイアグラムに配置する。  
  
- ビジネス ロジックやユーザー入力に基づいて図形の動作を管理する。  
  
- ダイアグラムの視覚エフェクト (パン、ズームなど) を制御する。  
  
- アプリケーション UI をカスタマイズする。  
  
- 外部データを Visio にインポートし、図形にリンクしてページ上にグラフィカルに表示する。  
  
  詳細な手順を表示してコードを Visio のオブジェクト モデルを使用して図面および図形を使用する例[Visio ドキュメントを操作](../vsto/working-with-visio-documents.md)と[Visio 図形を操作する](../vsto/working-with-visio-shapes.md)します。  
  
  VSTO アドインから Visio オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application` フィールドは、Visio の現在のインスタンスを表す `Microsoft.Office.Interop.Visio.Application` オブジェクトを返します。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
  Visio オブジェクト モデルを呼び出すときは、Visio のプライマリ相互運用機能アセンブリ (PIA) に用意された型を使用します。 PIA は、VSTO アドインのマネージド コードと Visio の COM オブジェクト モデルとの橋渡し役として機能します。 Visio PIA のすべての型は、`Microsoft.Office.Interop.Visio` 名前空間で定義されます。 プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)します。  
  
## <a name="visio-object-model-overview"></a>Visio オブジェクト モデルの概要  
 Visio オブジェクト モデルの概要を参照できます[Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)、Visio オブジェクト モデルのリファレンスや Sdk へのリンクが含まれます。  
  
## <a name="customize-the-user-interface-of-visio"></a>Visio のユーザー インターフェイスをカスタマイズします。  
 Visio の UI には、次のようなカスタマイズ オプションがあります。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|リボンをカスタマイズします。|[リボンの概要](../vsto/ribbon-overview.md)|  
  
 Visio の UI をカスタマイズする方法の詳細については、 [Visio.UIObject](/office/vba/api/Visio.UIObject) クラスの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Office 開発における Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199017)  
  