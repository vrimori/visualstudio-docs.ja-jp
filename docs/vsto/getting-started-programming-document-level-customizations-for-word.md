---
title: "Word 用のドキュメント レベルのカスタマイズのプログラミングについて | Microsoft Docs"
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
  - "Word プロジェクト [Visual Studio での Office 開発], はじめに"
  - "Visual Studio の Word ソリューション"
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Word 用のドキュメント レベルのカスタマイズのプログラミングについて
  ここでは、Microsoft Office Wordのドキュメント レベルのカスタマイズをVisual Studioを使用して作成する場合に必要な事項について説明します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## Word 用のドキュメント レベルのカスタマイズが動作するしくみについて  
 作成する各 Word のカスタマイズは 1 つの文書に基づいています。  カスタマイズの使用を開始する場合、エンド ユーザーは文書を開くか、または Word テンプレートから文書を作成します。  特定の領域へのカーソルの移動やボタンまたはメニュー項目のクリックなど、文書内で発生するイベントによって、アセンブリのイベント処理メソッドを呼び出すことができます。  文書を閉じると、カスタマイズで提供される機能は Word で使用できなくなります。  
  
 詳細については、「[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)」を参照してください。  
  
## Word 用のドキュメント レベルのプロジェクトの作成  
 Word のドキュメント レベルのカスタマイズ プロジェクトを作成するには、**\[新しいプロジェクト\]** ダイアログ ボックスで Word 文書または Word テンプレートのプロジェクト テンプレートを使用します。  これらのテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  
  
 Word 用のドキュメント レベルのプロジェクトを作成する方法の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  プロジェクト テンプレートの詳細については、「[Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)」を参照してください。  
  
## ホスト項目とホスト コントロールによる Word 文書のプログラミング  
 *ホスト項目*と*ホスト コントロール*は、ドキュメント レベルのカスタマイズのプログラミング モデルを提供するクラスです。  
  
 ホスト項目は、コードのエントリ ポイントを提供し、ホスト コントロールおよびWindowsフォーム コントロールのコンテナーとして機能できます。  Word のドキュメント レベルのプロジェクトでは、ホスト項目は `ThisDocument` クラスで表されます。  
  
 ホスト コントロールは、コンテンツ コントロール、ブックマーク、XML ノードなどのネイティブな Word オブジェクトに基づきます  ホスト コントロールはネイティブな Word オブジェクトと類似する機能を提供し、新しいイベント、デザイナー サポート、およびデータ バインディング機能も備えています。  プロジェクト コードおよび IntelliSense にファーストクラス オブジェクトとして現れるので、コードから特定のオブジェクトを簡単に直接参照できます。Word オブジェクト モデル全体を探す必要はありません。  
  
 詳細については、次のトピックを参照してください。  
  
-   [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)  
  
-   [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
## Word のユーザー インターフェイスのカスタマイズ  
 ほとんどの Microsoft Office ソリューションは、Office アプリケーションのユーザー インターフェイス \(UI\) を変更してユーザーがソリューションを操作できるようにします。  ドキュメント レベルのカスタマイズを使用して Word の UI を変更するには、さまざまな方法があります。  たとえば、リボンにコントロールを追加したり操作ウィンドウを表示できます。  詳細については、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。  
  
 プロジェクトに関連付けられている文書は Visual Studio で直接開くこともできます。  Visual Studio で文書を開いた場合は、Word ユーザー インターフェイスを使用して文書を変更できます。  文書をデザイン サーフェイスとして使用する場合は、コントロールを文書にドラッグできます。  詳細については、「[Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)」を参照してください。  
  
## データへのコントロールのバインディング  
 コンテンツ コントロールと <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは **\[データ ソース\]** ウィンドウのコントロール一覧に表示され、そこからドラッグできます。  この方法でコンテンツ コントロールやブックマークを追加すると、それらは \[データ ソース\] ウィンドウで設定したデータ ソースに自動的にバインドされます。  コードを記述せずに、データベース、サービス、およびビジネス オブジェクトのデータを表示できます。  詳細については、「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」を参照してください。  
  
## 次の手順  
 Word 用のドキュメント レベルのカスタマイズを作成する方法については、「[チュートリアル : 初めての Word 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)」を参照してください。  このチュートリアルでは、Visual Studio の Office 開発ツール、および Word 用のドキュメント レベルのカスタマイズのプログラミング モデルを紹介します。  
  
 Word プロジェクトの一般的なタスクを解説しているトピックの一覧については、「[Office プログラミングの共通タスク](../vsto/common-tasks-in-office-programming.md)」を参照してください。  
  
## 参照  
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [Word ソリューション](../vsto/word-solutions.md)   
 [チュートリアル : 初めての Word 用ドキュメント レベルのカスタマイズの作成](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)  
  
  