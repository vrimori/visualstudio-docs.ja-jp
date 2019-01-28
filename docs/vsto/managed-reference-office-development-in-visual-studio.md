---
title: マネージ参照 (Visual Studio での Office 開発)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aba08ad315c9e3165728b01c552c888f53c94a62
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871612"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>マネージ参照 (Visual Studio での Office 開発)
  このセクションには、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を対象とする Office プロジェクトで使用される名前空間と型についての API リファレンス ドキュメントが含まれています。 名前空間と、.NET Framework 3.5 を対象とする Office プロジェクトで使用されている型に関する API リファレンス ドキュメントについて、Visual Studio ドキュメントのリファレンス セクションを参照してください: [ http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)します。  
  
> [!NOTE]  
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、HTML5、JavaScript、CSS3、XML などのほぼすべての web プログラミング テクノロジを使用して、ビルドすることができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 <xref:Microsoft.Office.Tools>  
 Office ソリューションのプログラミングに共通するクラスが含まれています。 これには、VSTO アドインの基底クラス、VSTO アドインにカスタム作業ウィンドウを作成するクラス、Excel および Word ソリューションにスマート タグを作成するクラス、ドキュメント レベルのカスタマイズで操作ウィンドウを作成するクラスが含まれます。  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Excel のソリューションで使用できるホスト コントロールとホスト項目が含まれています。  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Excel のソリューションで使用できる Excel コントロールと Windows フォーム コントロールが含まれています。  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Outlook 用 VSTO アドインで使用されるクラスが含まれています。カスタム フォーム領域の作成に使用されるクラスも含まれています。  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 リボン デザイナーを使用して作成されたリボンのカスタマイズを、プログラムによって変更するために使用されるクラスが含まれています。  
  
 <xref:Microsoft.Office.Tools.Word>  
 Word のソリューションで使用できるホスト コントロールとホスト項目が含まれています。  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Word のソリューションで使用できる Word コントロールと Windows フォーム コントロールが含まれています。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスと、関連するキャッシュ データ クラスのセットが含まれています。 これらのクラスは、Microsoft Office がインストールされていないコンピューター上のドキュメント レベルのカスタマイズの特定部分を変更するために使用できます。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> インターフェイス (Office ソリューションの *配置後アクション* の作成用に実装可能)、Office ソリューションのインストール中にスローされる可能性のある例外、Visual Studio インフラストラクチャの一部である他の API が含まれています。  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]によってスローされる可能性のある大部分の例外、ドキュメント レベルのカスタマイズでデータのキャッシュに使用できるクラス、Visual Studio インフラストラクチャの一部であるその他の API が含まれています。  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Office プロジェクトのビルドに使用される MSBuild タスク クラスが含まれています。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のツール for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)  
