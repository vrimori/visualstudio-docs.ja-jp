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
ms.openlocfilehash: c583108d1cc7aca35b8df4f20d787571c865e400
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767817"
---
# <a name="visio-solutions"></a>Visio ソリューション
  Visual Studio には、Microsoft Office Visio の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Visio の自動化、Visio 機能の拡張、または Visio ユーザー インターフェイス (UI) のカスタマイズが可能です。  
  
 詳細については、VSTO アドインは、次を参照してください。 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)と[アーキテクチャの VSTO アドイン](../vsto/architecture-of-vsto-add-ins.md)です。Microsoft Office でのプログラミングに慣れていない場合は、次を参照してください。[開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)です。  
  
 **対象:** このトピックの情報は、Visio 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクトの種類別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="automate-visio-by-using-the-visio-object-model"></a>Visio オブジェクト モデルによる Visio を自動化します。  
 Visio オブジェクト モデルでは、組織図、フローチャート、プロジェクト タイムライン、ネットワーク ダイアグラム、事務所スペースなどのダイアグラムを Visio で自動的に作成するために使用できる多数のクラスが公開されています。 この API を使用して、次のような一般的なタスクを実行するコードを作成できます。  
  
-   図形やテキストを作成し、ダイアグラムに配置する。  
  
-   ビジネス ロジックやユーザー入力に基づいて図形の動作を管理する。  
  
-   ダイアグラムの視覚エフェクト (パン、ズームなど) を制御する。  
  
-   アプリケーション UI をカスタマイズする。  
  
-   外部データを Visio にインポートし、図形にリンクしてページ上にグラフィカルに表示する。  
  
 詳細な手順を表示し、Visio のオブジェクト モデルを使用して図面および図形を操作する例をコーディングすることができます[Visio 図面の操作](../vsto/working-with-visio-documents.md)と[Visio 図形を操作する](../vsto/working-with-visio-shapes.md)です。  
  
 VSTO アドインから Visio オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application` フィールドは、Visio の現在のインスタンスを表す `Microsoft.Office.Interop.Visio.Application` オブジェクトを返します。 詳細については、次を参照してください。[プログラムは、VSTO アドイン](../vsto/programming-vsto-add-ins.md)です。  
  
 Visio オブジェクト モデルを呼び出すときは、Visio のプライマリ相互運用機能アセンブリ (PIA) に用意された型を使用します。 PIA は、VSTO アドインのマネージ コードと Visio の COM オブジェクト モデルとの橋渡し役として機能します。 Visio PIA のすべての型は、`Microsoft.Office.Interop.Visio` 名前空間で定義されます。 プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
## <a name="visio-object-model-overview"></a>Visio オブジェクト モデルの概要  
 Visio オブジェクト モデルの概要を知ることができます[Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)、Visio オブジェクト モデルのリファレンスや Sdk へのリンクが含まれます。  
  
## <a name="customize-the-user-interface-of-visio"></a>Visio のユーザー インターフェイスをカスタマイズします。  
 Visio の UI には、次のようなカスタマイズ オプションがあります。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|リボンをカスタマイズします。|[リボンの概要](../vsto/ribbon-overview.md)|  
  
 Visio の UI をカスタマイズする方法の詳細については、 [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) クラスの VBA リファレンス ドキュメントを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)   
 [Office 開発における Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199017)  
  