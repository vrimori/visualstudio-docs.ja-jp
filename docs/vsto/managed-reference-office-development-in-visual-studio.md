---
title: "マネージ参照 (Visual Studio での Office 開発) |Microsoft ドキュメント"
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
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3304d104a0ccf308c02a770f3e79fb08f6d06049
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="managed-reference-office-development-in-visual-studio"></a>マネージ参照 (Visual Studio での Office 開発)
  このセクションには、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を対象とする Office プロジェクトで使用される名前空間と型についての API リファレンス ドキュメントが含まれています。 .NET Framework 3.5 を対象とする Office プロジェクトで使用される名前空間と型に関する API リファレンス ドキュメントについては、Visual Studio ドキュメントのリファレンス セクション ( [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)) をご覧ください。  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
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
  
## <a name="see-also"></a>参照  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [作業の開始 (&) #40 です。 Visual Studio &#41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  