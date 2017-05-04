---
title: "方法 : ワークシートに XMLMappedRange コントロールを追加する | Microsoft Docs"
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
  - "コントロール [Visual Studio での Office 開発], 追加 (ワークシートに)"
  - "XMLMappedRange コントロール, 追加 (ワークシートに)"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 方法 : ワークシートに XMLMappedRange コントロールを追加する
  XML 要素を Microsoft Office Excel のセルに割り当てると、Visual Studio によって自動的に <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールがワークシートに追加されます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールは、**ツールボックス**や **\[データ ソース\]** ウィンドウにはありません。  また、<xref:Microsoft.Office.Tools.Excel.XmlMappedRange> コントロールをプログラミングによって作成することもできません。  
  
### XMLMappedRange コントロールをワークシートに追加するには  
  
1.  Visual Studio デザイナーで、Excel ブックを開きます。  
  
2.  コントロールを追加するワークシートを開きます。  
  
3.  **\[開発\]** タブで **\[ソース\]** をクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブがリボンに表示されていない場合は、表示する必要があります。  詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
     **\[XML ソース\]** 作業ウィンドウが表示されます。  
  
4.  **\[XML ソース\]** 作業ウィンドウで **\[XML の対応付け\]** をクリックします。  
  
5.  **\[XML の対応付け\]** ダイアログ ボックスで、**\[追加\]** をクリックします。  
  
     **\[XML ソース\]** ダイアログ ボックスが表示されます。  
  
6.  **\[XML ソース\]** ダイアログ ボックスで XML スキーマを選択し、**\[開く\]** をクリックします。  
  
     **\[XML の対応付け\]** ダイアログ ボックスにスキーマが追加されます。  
  
7.  **\[XML の対応付け\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
8.  **\[XML ソース\]** 作業ウィンドウから、要素をワークシートのセルにドラッグします。  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> が作成され、プロジェクトに追加されます。  
  
    > [!NOTE]  
    >  **\[XML ソース\]** 作業ウィンドウから親要素をドラッグすると、<xref:Microsoft.Office.Tools.Excel.ListObject> コントロールが作成されます。  
  
## 参照  
 [XmlMappedRange コントロール](../vsto/xmlmappedrange-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [方法 : Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  