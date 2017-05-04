---
title: "Office プロジェクトのプロパティ | Microsoft Docs"
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
  - "[アセンブリの場所の信頼] プロパティ"
  - "ドキュメントのキャッシュ プロパティ"
  - "プロパティ [Visual Studio での Office 開発]"
  - "名前空間 (Host Item プロパティの)"
  - "Office プロジェクト [Visual Studio での Office 開発]、プロパティ"
  - "プロジェクト [Visual Studio での Office 開発]、プロパティ"
  - "Value2 プロパティ"
ms.assetid: 1284d6c3-8200-4151-88ce-0b5c7765af25
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Office プロジェクトのプロパティ
  Visual Studio で Office プロジェクトに使用できる重要なプロパティがいくつかあります。 これらのプロパティには \[**プロパティ**\] ウィンドウでアクセスできます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## ホスト項目の名前空間  
 Visual C\# プロジェクトでホスト項目クラス \(たとえば、`ThisAddIn`、`ThisWorkbook`、`ThisDocument` クラス\) の名前空間を変更するには、\[**ホスト項目の名前空間**\] プロパティを使用します。 このプロパティは、**ソリューション エクスプローラー**でドキュメント レベル プロジェクト \(ExcelWorkbook1.xlsx や WordDocument1.docx など\) のドキュメント ノードを選択するか、または VSTO アドイン プロジェクト \(Excel や Word など\) のアプリケーション ノードを選択した場合に、**\[プロパティ\]** ウィンドウに表示されます。  
  
 Visual C\# Office プロジェクトを作成すると、プロジェクトの名前に基づいてホスト項目に名前空間が与えられます。 コード ファイルを直接編集するのではなく、\[**ホスト項目の名前空間**\] プロパティを使用して名前空間を変更することをお勧めします。 このプロパティを使用すると、名前空間は、生成されるコード ファイル \(非表示\) だけでなく、表示されるコード ファイル内でも変更されます。  
  
## CacheInDocument  
 **CacheInDocument** プロパティは、Visual Studio デザイナーで <xref:System.Data.DataSet> のインスタンスを選択すると、ドキュメント レベルのプロジェクトの \[**プロパティ**\] ウィンドウに表示されます。 パブリック メンバーだけがキャッシュされます。<xref:System.Data.DataSet> をキャッシュする場合は、\[**Modifiers**\] プロパティを \[**Public**\] に設定してください。  
  
 このプロパティはブール値を受け取ります。  
  
-   ドキュメント内のデータセットをキャッシュする場合は、**true** を選択します。  
  
-   ドキュメントのデータセットをキャッシュしない場合は、**false** を選択します。  
  
 データのキャッシュの詳細については、「[ドキュメント レベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)」を参照してください。  
  
## Value2  
 **Value2** プロパティは、Excel ブック プロジェクトまたはテンプレート プロジェクトにのみ使用できます。 ワークシート デザイナーで <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを選択すると、\[**プロパティ**\] ウィンドウの **Databindings** プロパティの下に表示されます。  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> の <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> プロパティをデータ ソースのフィールドにバインドするには、\[**プロパティ**\] ウィンドウの **Value2** プロパティを使用します。  
  
## 参照  
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)   
 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)  
  
  