---
title: "PowerPoint ソリューション |Microsoft ドキュメント"
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
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de978f92a5c410312cac00034006cd698b1c5cea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="powerpoint-solutions"></a>PowerPoint ソリューション
  Visual Studio には、Microsoft Office PowerPoint の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用すると、PowerPoint の自動化、PowerPoint 機能の拡張、PowerPoint ユーザー インターフェイス (UI) のカスタマイズが可能です。  
  
 VSTO アドインの詳細については、「 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 」および「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。Microsoft Office でのプログラミングに慣れていない場合は、次を参照してください。[作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)です。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[操作方法: 作成アドインで PowerPoint 用?](http://go.microsoft.com/fwlink/?LinkId=132767)です。  
  
## <a name="automating-powerpoint-by-using-the-powerpoint-object-model"></a>PowerPoint のオブジェクト モデルを使用した PowerPoint の自動化  
 PowerPoint オブジェクト モデルでは、PowerPoint の自動化に使用できる型が多数公開されています。 それらの型によって、次のような一般的なタスクを実行するコードを作成できます。  
  
-   プログラムによるプレゼンテーションの作成と書式指定  
  
-   プレゼンテーションへのスライドの追加または削除  
  
-   スライドへの図形の追加または変更  
  
 VSTO アドインから PowerPoint オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application` フィールドは PowerPoint の現在のインスタンスを表す <xref:Microsoft.Office.Interop.PowerPoint.Application> オブジェクトを返します。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
 PowerPoint オブジェクト モデルを呼び出すときには、PowerPoint のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージ コードと PowerPoint の COM オブジェクト モデルとの仲介役を果たします。 PowerPoint プライマリ相互運用機能アセンブリ内の型は、すべて <xref:Microsoft.Office.Interop.PowerPoint> 名前空間に定義されています。 プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)と[Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
##  <a name="WordOMDocumentation"></a> PowerPoint オブジェクト モデル ドキュメントの使用  
 PowerPoint オブジェクト モデルの詳細については、PowerPoint プライマリ相互運用機能アセンブリ (PIA) のリファレンスと、VBA オブジェクト モデルのリファレンスを参照してください。  
  
### <a name="primary-interop-assembly-reference"></a>プライマリ相互運用機能アセンブリのリファレンス  
 PowerPoint PIA のリファレンス ドキュメントは、PowerPoint のプライマリ相互運用機能アセンブリの型について説明しています。 このドキュメントは、「 [PowerPoint 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189588)」から入手できます。  
  
 PIA のクラスとインターフェイスの違い、PIA のイベントの実装方法など、PowerPoint PIA の設計の詳細については、「 [Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=199885)」を参照してください。  
  
### <a name="vba-object-model-reference"></a>VBA オブジェクト モデルのリファレンス  
 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される PowerPoint オブジェクト モデルについて説明しています。 詳細については、「 [PowerPoint 2010 オブジェクト モデルのリファレンス](http://go.microsoft.com/fwlink/?LinkId=199770)」を参照してください。  
  
 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、PowerPoint プライマリ相互運用機能アセンブリ (PIA) の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンス内のプレゼンテーション オブジェクトに対応しています。、 <xref:Microsoft.Office.Interop.PowerPoint.Presentation> 、PowerPoint pia の型。 VBA オブジェクト モデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例を紹介しています。ただし、Visual Studio を使用して作成した PowerPoint VSTO アドイン プロジェクトでこのリファレンス内の VBA コードを使用するには、それらを Visual Basic または Visual C# に変換する必要があります。  
  
## <a name="customizing-the-user-interface-of-powerpoint"></a>PowerPoint のユーザー インターフェイスのカスタマイズ  
 PowerPoint の UI を次のように変更できます。  
  
|タスク|詳細情報|  
|----------|--------------------------|  
|カスタム作業ウィンドウを作成する。|[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)|  
|リボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|  
|リボン上の組み込みタブにカスタム グループを追加する。|[方法: 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 PowerPoint の UI およびその他の Microsoft Office アプリケーションのカスタマイズの詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: 初めての PowerPoint 用 VSTO の追加の作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office 開発における PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  