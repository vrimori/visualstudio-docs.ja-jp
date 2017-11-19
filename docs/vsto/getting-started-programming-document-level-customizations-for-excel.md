---
title: "Excel 用ドキュメント レベル カスタマイズのプログラミング |Microsoft ドキュメント"
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
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1755aa5c8e54bd1b84e0f88ea70b4163f3a87af6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Excel のドキュメント レベルのカスタマイズのプログラミングの概要
  だけを開始する Visual Studio を使用して Microsoft Office Excel のドキュメント レベルのカスタマイズを作成する場合に、知っておく次に示します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>Excel の作業用のドキュメント レベルのカスタマイズを理解します。  
 Excel 用ドキュメント レベルのカスタマイズは、1 つのブックに基づいています。 カスタマイズを使用するには、エンドユーザーはブックを開くまたは Excel テンプレートからブックを作成します。 たとえばのセルに入力するか、ボタンおよびメニュー項目をクリックすると、ブック内のイベントは、アセンブリ内のイベント処理メソッドを呼び出すことができます。 ブックが閉じられたときに、カスタマイズによって提供される機能は Excel に含まれているドキュメントでのみ使用できますではなくなりました。  
  
 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)です。  
  
## <a name="creating-document-level-projects-for-excel"></a>Excel 用ドキュメント レベルのプロジェクトを作成します。  
 Excel 用ドキュメント レベルのカスタマイズを作成するに Excel ブックまたは Excel テンプレート プロジェクト テンプレートを使用して、**新しいプロジェクト** ダイアログ ボックス。 これらのテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  
  
 Excel のドキュメント レベルのプロジェクトを作成する方法の詳細については、次を参照してください。[する方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)です。 プロジェクト テンプレートの詳細については、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)です。  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>ホスト項目とホスト コントロールを使用して Excel ブックのプログラミング  
 *ホスト項目*と*ホスト コントロール*Visual Studio を使用して作成されたドキュメント レベルのカスタマイズのプログラミング モデルを提供するクラスです。  
  
 ホスト項目が、コードのエントリ ポイントを提供し、ホスト コントロールと Windows フォーム コントロールのコンテナーとしても機能できます。 Excel 用ドキュメント レベルのプロジェクトでこれらのホスト項目がによって表される、 `ThisWorkbook`、 `Sheet1`、 `Sheet2`、および`Sheet3`クラスです。  
  
 ホスト コントロールは、リスト オブジェクトや範囲など、ネイティブな Excel オブジェクトに基づきます。 ホスト コントロールは、ネイティブな Excel オブジェクトと同様の機能を提供し、新しいイベント、デザイナー サポート、およびデータ バインディング機能も備えています。 プロジェクト コードでは、IntelliSense で、Excel オブジェクト モデルを移動することがなく、コード内で直接特定のオブジェクトを参照するが容易で最上位のオブジェクトとして表示されます。  
  
 詳細については、次のトピックを参照してください。  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>Excel のユーザー インターフェイスのカスタマイズ  
 ほとんどの Microsoft Office ソリューションでは、ソリューションとの対話をユーザーに対していくつかの方法を提供する、Office アプリケーションのユーザー インターフェイス (UI) を変更します。 ドキュメント レベルのカスタマイズを使用して、Excel の UI を変更するには、多くの方法はあります。 たとえば、コントロールを追加するには、リボンにまたは操作ウィンドウを表示することができます。 詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
 Visual Studio で直接、プロジェクトに関連付けられているブックを開くこともできます。 ブック Visual Studio で開く場合に、Excel ユーザー インターフェイスを使用してブックを変更することができます。 コントロールをワークシートにドラッグすることにより、デザイン サーフェイスとして、ブックを使用することもできます。 詳細については、次を参照してください。 [Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)です。  
  
## <a name="using-data-binding"></a>データ バインディングの使用  
 ホスト コントロールにもからドラッグできるコントロールのリスト、**データソース**ウィンドウです。 このように自動的にホスト コントロールを追加するウィンドウを使用し、設定したデータ ソースにバインドします。 コードを記述せずには、データベース、web サービス、およびビジネス オブジェクトのデータを表示することができます。 詳細については、次を参照してください。 [Office ソリューションでのコントロールへのデータ バインディング](../vsto/binding-data-to-controls-in-office-solutions.md)です。  
  
## <a name="next-steps"></a>次の手順  
 Excel 用ドキュメント レベルのカスタマイズを作成する方法については、次を参照してください。[チュートリアル: を作成する、初めてドキュメント レベルのカスタマイズ for Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)です。 このチュートリアルでは、Visual Studio と Excel のドキュメント レベルのカスタマイズのプログラミング モデルでの Office 開発ツールについて説明します。  
  
 Excel プロジェクトの一般的なタスクを解説しているトピックの一覧は、次を参照してください。 [Office プログラミングで一般的なタスク](../vsto/common-tasks-in-office-programming.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [Excel ソリューション](../vsto/excel-solutions.md)   
 [チュートリアル: 初めての Excel 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [使用して Excel のチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)  
  
  