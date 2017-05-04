---
title: "Excel のドキュメント レベルのカスタマイズのプログラミングの概要 | Microsoft Docs"
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
  - "Excel プロジェクト [Visual Studio での Office 開発], はじめに"
  - "Visual Studio の Excel ソリューション"
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Excel のドキュメント レベルのカスタマイズのプログラミングの概要
  ここでは、Microsoft Office Excel用のドキュメント レベルのカスタマイズをVisual Studioを使用して作成する場合に必要な事項について説明します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## Excel 用のドキュメント レベルのカスタマイズが動作するしくみについて  
 Excel 用のドキュメント レベルのカスタマイズは単一のブックに基づいています。  カスタマイズの使用を開始する場合、エンド ユーザーはブックを開くか、Excel テンプレートからブックを作成します。  セルへの入力やボタンまたはメニュー項目のクリックなど、ブック内で発生するイベントによって、アセンブリのイベント処理メソッドを呼び出すことができます。  ブックを閉じると、カスタマイズで提供される機能はExcelで使用できなくなり、のみを含むドキュメントではありません。  
  
 詳細については、「[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)」を参照してください。  
  
## Excel 用のドキュメント レベルのプロジェクトの作成  
 Excel 用のドキュメント レベルのカスタマイズを作成するには、**\[新しいプロジェクト\]** ダイアログ ボックスで Excel ブックまたは Excel テンプレートのプロジェクト テンプレートを使用します。  これらのテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  
  
 Excel 用のドキュメント レベルのプロジェクトを作成する方法の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  プロジェクト テンプレートの詳細については、「[Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)」を参照してください。  
  
## ホスト項目とホスト コントロールによる Excel ブックのプログラミング  
 *ホスト項目* と *ホスト コントロールは*、Visual Studioを使用して作成されたドキュメント レベルのカスタマイズのプログラミング モデルを提供するクラスです。  
  
 ホスト項目は、コードのエントリ ポイントを提供し、ホスト コントロールおよびWindowsフォーム コントロールのコンテナーとして機能できます。  Excel 用のドキュメント レベルのプロジェクトでは、これらのホスト項目は `ThisWorkbook`、`Sheet1`、`Sheet2`、および `Sheet3` の各クラスによって表されます。  
  
 ホスト コントロールは、リスト オブジェクトや範囲などのネイティブな Excel オブジェクトに基づきます  ホスト コントロールはネイティブな Excel オブジェクトと類似する機能を提供し、新しいイベント、デザイナー サポート、およびデータ バインディング機能も備えています。  プロジェクト コードおよび IntelliSense にファーストクラス オブジェクトとして現れるので、コードから特定のオブジェクトを簡単に直接参照できます。Excel オブジェクト モデル全体を探す必要はありません。  
  
 詳細については、次のトピックを参照してください。  
  
-   [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)  
  
-   [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
## Excel のユーザー インターフェイスのカスタマイズ  
 ほとんどの Microsoft Office ソリューションは、Office アプリケーションのユーザー インターフェイス \(UI\) を変更してユーザーがソリューションを操作できるようにします。  ドキュメント レベルのカスタマイズを使用して Excel の UI を変更するには、さまざまな方法があります。  たとえば、リボンにコントロールを追加したり、操作ウィンドウを表示できます。  詳細については、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。  
  
 プロジェクトに関連付けられているブックは Visual Studio で直接開くこともできます。  Visual Studio でブックを開いた場合は、Excel ユーザー インターフェイスを使用してブックを変更できます。  ブックをデザイン サーフェイスとして使用する場合は、コントロールをワークシートにドラッグできます。  詳細については、「[Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)」を参照してください。  
  
## データ連結の使用  
 ホスト コントロールは、**\[データ ソース\]** ウィンドウのコントロール一覧にも表示されるので、一覧からドラッグできます。  この方法でホスト コントロールを追加すると、ホスト コントロールはウィンドウで設定したデータ ソースに自動的にバインドされます。  コードを記述せずに、データベース、Webサービス、およびビジネス オブジェクトのデータを表示できます。  詳細については、「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」を参照してください。  
  
## 次の手順  
 Excel 用のドキュメント レベルのカスタマイズを作成する方法については、「[チュートリアル : 初めての Excel 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)」を参照してください。  このチュートリアルでは、Visual Studio の Office 開発ツール、および Excel 用のドキュメント レベルのカスタマイズのプログラミング モデルを紹介します。  
  
 Excel プロジェクトの一般的なタスクを解説しているトピックの一覧については、「[Office プログラミングの共通タスク](../vsto/common-tasks-in-office-programming.md)」を参照してください。  
  
## 参照  
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [Excel ソリューション](../vsto/excel-solutions.md)   
 [チュートリアル : 初めての Excel 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)  
  
  