---
title: PowerPoint ソリューション
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26e1da711ebe3b0359a73894d729f79124e88aaf
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875018"
---
# <a name="powerpoint-solutions"></a>PowerPoint ソリューション
  Visual Studio には、Microsoft Office PowerPoint の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用すると、PowerPoint の自動化、PowerPoint 機能の拡張、PowerPoint ユーザー インターフェイス (UI) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、次を参照してください。 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)と[Architecture of VSTO アドイン](../vsto/architecture-of-vsto-add-ins.md)します。Microsoft Office を使用したプログラミングに慣れていない場合は、次を参照してください。[開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)します。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、HTML5、JavaScript、CSS3、XML などのほぼすべての web プログラミング テクノロジを使用して、ビルドすることができます。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i:。Microsoft PowerPoint のアドインを作成しますか。](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>PowerPoint オブジェクト モデルを使用して PowerPoint を自動化します。  
 PowerPoint オブジェクト モデルでは、PowerPoint の自動化に使用できる型が多数公開されています。 それらの型によって、次のような一般的なタスクを実行するコードを作成できます。  
  
- プログラムによるプレゼンテーションの作成と書式指定  
  
- プレゼンテーションへのスライドの追加または削除  
  
- スライドへの図形の追加または変更  
  
  VSTO アドインから PowerPoint オブジェクト モデルにアクセスするには、使用、`Application`のフィールド、`ThisAddIn`プロジェクト内のクラス。 `Application` フィールドは PowerPoint の現在のインスタンスを表す <xref:Microsoft.Office.Interop.PowerPoint.Application> オブジェクトを返します。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
  PowerPoint オブジェクト モデルを呼び出すときには、PowerPoint のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージド コードと PowerPoint の COM オブジェクト モデルとの仲介役を果たします。 PowerPoint プライマリ相互運用機能アセンブリ内の型は、すべて <xref:Microsoft.Office.Interop.PowerPoint> 名前空間に定義されています。 プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)します。  
  
##  <a name="WordOMDocumentation"></a> PowerPoint オブジェクト モデル ドキュメントを使用します。  
 PowerPoint オブジェクト モデルの詳細については、PowerPoint プライマリ相互運用機能アセンブリ (PIA) のリファレンスと、VBA オブジェクト モデルのリファレンスを参照してください。  
  
### <a name="primary-interop-assembly-reference"></a>プライマリ相互運用機能アセンブリのリファレンス  
 PowerPoint PIA のリファレンス ドキュメントは、PowerPoint のプライマリ相互運用機能アセンブリの型について説明しています。 このドキュメントは、次の場所から入手できます。[PowerPoint 2010 プライマリ相互運用機能アセンブリ リファレンス](http://go.microsoft.com/fwlink/?LinkId=189588)します。  
  
 PIA のイベントの実装方法、PIA のクラスとインターフェイスの違いなど、PowerPoint PIA の設計に関する詳細情報を参照してください[Office プライマリ相互運用機能アセンブリのクラスおよびインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=199885)。  
  
### <a name="vba-object-model-reference"></a>VBA オブジェクト モデル リファレンス  
 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される PowerPoint オブジェクト モデルについて説明しています。 詳細については、次を参照してください[PowerPoint 2010 オブジェクト モデル リファレンス。](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、PowerPoint プライマリ相互運用機能アセンブリ (PIA) の型とメンバーに対応します。 VBA オブジェクト モデルのリファレンス内の Presentation オブジェクトが対応するなど、 <xref:Microsoft.Office.Interop.PowerPoint.Presentation> PowerPoint PIA の型。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した PowerPoint VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>PowerPoint のユーザー インターフェイスをカスタマイズします。  
 PowerPoint の UI を次のように変更できます。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
|リボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
|リボン上の組み込みタブにカスタム グループを追加する。|[方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 UI の PowerPoint およびその他の Microsoft Office アプリケーションをカスタマイズする方法の詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Powerpoint の場合、最初の VSTO アドインの作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [VSTO アドインのプログラミングを始める](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office 開発における PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199015)  
