---
title: "Visual Studio 環境における Office プロジェクト"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.WordDocument"
  - "VST.ProjectItem.ExcelWorkbook"
  - "VST.ProjectItem.ExcelTemplate"
  - "VST.ProjectItem.ExcelSheet"
  - "VST.ProjectItem.BlueprintCode"
  - "VST.ProjectItem.Word"
  - "VST.ProjectItem.Excel"
  - "VST.ProjectItem.AddinProject"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner"
  - "VST.ProjectItem.ExtendedBluePrint"
  - "VST.ProjectItem.WordTemplate"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner"
  - "VST.Designer.ExcelVST.Designer.Word"
  - "VST.ProjectItem.ExtendedBlueprintCode"
  - "VST.ProjectItem.BluePrint"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ドキュメント [Visual Studio での Office 開発]"
  - "隠しファイル [Visual Studio での Office 開発]"
  - "プロジェクト ファイル [Visual Studio での Office 開発]、非表示"
  - "Visual Studio での Office 開発、Visual Studio のドキュメント"
  - "デザイン ビュー、Excel"
  - "デザイナー、Visual Studio での Office 開発"
  - "Office ドキュメント [Visual Studio での Office 開発"
  - "Office ドキュメント [Visual Studio での Office 開発]、Visual Studio のドキュメントの概要"
  - "デザイナー [Visual Studio での Office 開発]"
  - "Word デザイナー"
  - "Word [Visual Studio での Office 開発]、Word デザイナー"
  - "Visual Studio、Office ドキュメント"
  - "ワークシート [Visual Studio での Office 開発]"
  - "VST.Designer.ExcelVST.Designer.Word"
ms.assetid: 4bff36c9-4edd-4b28-89e6-0ea9f6caca02
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Visual Studio 環境における Office プロジェクト
  Microsoft Office プロジェクトの開発環境は、Visual Studio の他の種類のプロジェクト \(Windows フォーム プロジェクトなど\) に似ています。 Office プロジェクトを作成したり、開いたりすると、**ソリューション エクスプローラー**にプロジェクト項目が表示されます。 ドキュメント レベルのプロジェクトの場合は、ドキュメント \(つまり、Word 文書または Excel ブック\) が Visual Studio で開かれ、ビジュアルなデザイナーとして動作します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## ソリューション エクスプローラーのプロジェクト項目  
 ドキュメント レベルのプロジェクトの場合、**ソリューション エクスプローラー**には次の既定の項目が表示されます。  
  
-   プロジェクトでカスタマイズされた文書、ブック、およびシートのノード。 これらのノードは、文書、ブック、およびシートに関連付けられたコード ファイルのコンテナーとして機能します。  
  
-   プロジェクトでカスタマイズされた文書、ブック、およびシートに関連付けられたコード ファイル。 Word プロジェクトの場合、コード ファイルは Word 文書またはテンプレートに関連付けられます。 Excel プロジェクトの場合、コード ファイルは Excel ブックまたはテンプレート、およびブックまたはテンプレート内の各ワークシートとグラフ シートに関連付けられます。  
  
-   直接編集することを意図していない非表示のプロジェクト ファイル。 詳細については、「[非表示のプロジェクト ファイル](#hiddenfiles)」を参照してください。  
  
 VSTO アドイン プロジェクトの場合、**ソリューション エクスプローラー**には次の既定の項目が表示されます。  
  
-   アプリケーション ノード。 このノードの名前は、ホスト アプリケーション \(**Word**、**Excel**、**Outlook** など\) と同じです。 アプリケーション ノードには ThisAddIn コード ファイルが含まれています。**ホスト項目の名前空間**プロパティも用意されています。 このプロパティの詳細については、「[Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)」を参照してください。  
  
-   ThisAddIn コード ファイル。 このファイルには、VSTO アドイン用に生成された `ThisAddIn` クラスが含まれています。 このクラスの詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
-   直接編集することを意図していない非表示のプロジェクト ファイル。 詳細については、「[非表示のプロジェクト ファイル](#hiddenfiles)」を参照してください。  
  
### 一時的な証明書  
 Office プロジェクトには、*プロジェクト名*\_TemporaryKey.pfx という名前の一時的な証明書も含まれています。 この証明書は、開発時にプロジェクトのアプリケーション マニフェストおよび配置マニフェストに署名するために使用します。 詳細については、次のトピックを参照してください。[Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md) および[Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> 非表示のプロジェクト ファイル  
 いくつかのプロジェクト ファイルは、既定では非表示です。 これらのファイルは Visual Studio によって生成され、プロジェクト タイプごとに異なります。 隠しファイルを表示するには、**ソリューション エクスプローラー**で **\[すべてのファイルを表示\]** をクリックします。  
  
 非表示のプロジェクト ファイルを変更しないでください。 これらのファイルを直接変更することはできません。変更すると、プロジェクトが破損するおそれがあります。 非表示のプロジェクト ファイルは、ドキュメントが変更されるたびに再生成されます。 非表示のプロジェクト ファイルを手動で変更しても、ファイルを再生成するときにその変更が失われます。  
  
## ドキュメント レベルのプロジェクト内のドキュメント デザイナー  
 Excel および Word のドキュメント レベルのプロジェクトには、Visual Studio 内のプロジェクトに関連付けられたドキュメントをホストするデザイナーが用意されています。 デザイナーでは、Visual Studio 環境から出ることなくドキュメントを変更できます。  
  
 ドキュメントをデザイナーで開くには、ドキュメントに関連付けられた**ソリューション エクスプローラー**でコード ファイルをダブルクリックします。 たとえば、Excel プロジェクトのワークシート **Sheet1** をデザイナーで開くには、**Sheet1** コード ファイルをダブルクリックします。  
  
 デザイナーでドキュメントを変更する場合、Office アプリケーションのネイティブ機能を利用できます。 たとえば、ドキュメントやワークシートにテキストを入力したり、リボンを使用してテーブルやグラフの追加などのタスクを実行したりできます。 既定では、ショートカット キーの割り当ては Visual Studio の割り当てに設定されています。 Office のショートカット キーの割り当てを代わりに使用するには、**\[ツール\]** メニューの **\[オプション\]** ダイアログ ボックスを開き、**\[Microsoft Office Keyboard 設定\]** ノードの設定を変更します。  
  
### ドキュメントのコントロール  
 Visual Studio の *\[ツールボックス\]* から**ホスト コントロール**や Windows フォーム コントロールをドキュメント デザイン サーフェイスにドラッグできます。 ホスト コントロール \(Word コンテンツ コントロール、Excel 範囲など\) は特殊なバージョンの Office オブジェクトで、Visual Studio を使用して作成された Office プロジェクトで使用できます。 ホスト コントロールには、対応する Office オブジェクトでは使用できない機能 \(データ バインド、追加イベントなど\) があります。  
  
 詳細については、[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md) および [Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md) を参照してください。  
  
### デザイナーでの Excel ワークシートとブック  
 ワークシートをデザイナーで開くと、Excel で直接開く場合と同じ方法でワークシートを変更できます。 ワークシート セルをダブルクリックすると、そのセルが編集モードに変わります。 ホスト コントロールを格納したセルをダブルクリックすると、コード エディターが開かれ、そのコントロールの既定のイベント ハンドラーが生成されます。 他のワークシートに移動するには、デザイナーの下部にあるワークシート タブをクリックします。  
  
 ブックをデザイナーで開いても、デザイン サーフェイスは表示されません。 ブックのデザイン ビューは、デザイナーの領域を占めている大きなコンポーネント トレイです。  
  
 ブックやブック内の各シートには、関連付けられたコード ファイルがあります。 各コード ファイルには、生成された*ホスト項目*クラスがあり、ブックまたはシートを表します。 詳細については、「[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)」を参照してください。  
  
### デザイナーでの Word 文書  
 文書をデザイナーで開くと、Word で直接開く場合と同じ方法で文書を変更できます。 文書内の単語をダブルクリックすると、その単語が選択されます。 ただし、単語がホスト コントロールの内部にある場合は、コード エディターが開かれ、そのコントロールの既定のイベント ハンドラーが生成されます。  
  
 文書には、関連付けられたコード ファイルがあります。 コード ファイルには、生成された*ホスト項目*クラスがあり、文書を表します。 詳細については、「[Document ホスト項目](../vsto/document-host-item.md)」を参照してください。  
  
### デザイン モードと実行時モード  
 Visual Studio 環境でドキュメントを開くと、常に*デザイン モード*になります。 ホスト コントロールをドキュメントにドラッグするなど、一部のタスクは、デザイン モードでのみ実行できます。  
  
 ドキュメントを*実行時モード*で表示するには、アプリケーションとドキュメントを Visual Studio の外部で開く必要があります。 また、プロジェクトをビルドおよび実行することもできます。その場合、ドキュメントとアプリケーションは Visual Studio の外部で自動的に開かれます。  
  
## コード エディター  
 コード エディターを使用すると、ソリューション内の表示コード ファイルを表示および変更できます。 これらのファイルには、ソリューションの動作を定義するコードが含まれています。  
  
 コード エディターの詳細については、「[コード エディターとテキスト エディターでのコードの作成](../ide/writing-code-in-the-code-and-text-editor.md)」を参照してください。 Office プロジェクトのコードを記述する方法の詳細については、「[Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)」を参照してください。  
  
## プロパティ ウィンドウ  
 **プロパティ** ウィンドウには、**ソリューション エクスプローラー**で選択されたプロジェクト項目のプロパティ、およびデザイナーで選択された UI 要素 \(ドキュメント レベル プロジェクトのコントロールや文書など\) のプロパティが表示されます。 アプリケーションとドキュメントに固有のプロパティと、すべてのプロジェクトで共通のプロパティがあります。  
  
## データ ソース ウィンドウ  
 ドキュメント レベルの Office プロジェクトで **データ ソース** ウィンドウを使用すると、データ ソースをドキュメントにドラッグし、そのデータ ソースにバインドされているコントロールを作成できます。 詳細については、「[Visual Studio でのデータへのコントロールのバインド](../Topic/Binding%20controls%20to%20data%20in%20Visual%20Studio.md)」を参照してください。  
  
## 参照  
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)  
  
  