---
title: "方法 : Visual Studio 内でワークシートにスキーマを割り当てる | Microsoft Docs"
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
  - "Excel [Visual Studio での Office 開発], XML スキーマ"
  - "マップ [Visual Studio での Office 開発], XML スキーマを Excel ワークシートに"
  - "ワークシート [Visual Studio での Office 開発], XML スキーマ"
  - "XML スキーマ [Visual Studio での Office 開発], マップ"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 方法 : Visual Studio 内でワークシートにスキーマを割り当てる
  Visual Studio でワークシートを開いているときに、ワークシートに XML スキーマを割り当てることができます。  Visual Studio の外部でブックを開いているときに使用するのと同じ Microsoft Office Excel ツールを使用します。  Excel ソリューションを作成する前にワークシートにスキーマを割り当てるか、作成した後に割り当てるかにかかわらず、Office プロジェクトは同じオブジェクトを作成します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Excel ソリューションでは、マルチパート XML スキーマは使用できません。  
  
### Visual Studio 内で Excel ワークシートに XML スキーマを割り当てるには  
  
1.  Visual Studio で、Excel ブックまたはテンプレート プロジェクトを開きます。  
  
2.  ワークシート内をクリックしてデザイナーからフォーカスを移動します。  
  
3.  リボンの **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。  詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
4.  **\[XML\]** グループで、**\[ソース\]** をクリックします。  
  
     **\[XML ソース\]** ウィンドウが表示されます。  
  
5.  **\[XML ソース\]** ウィンドウで **\[XML の対応付け\]** をクリックします。  
  
     **\[XML の対応付け\]** ダイアログ ボックスが表示されます。  
  
6.  **\[XML の対応付け\]** ダイアログ ボックスで、**\[追加\]** をクリックします。  
  
7.  目的のスキーマ ファイルに移動して選択し、**\[開く\]** をクリックします。  
  
8.  **\[OK\]** をクリックします。  
  
     **\[XML ソース\]** ウィンドウにスキーマが表されます。  プロジェクトで、型指定された <xref:System.Data.DataSet> がスキーマに基づいて生成され、<xref:System.Windows.Forms.BindingSource> が作成されます。  
  
9. **\[XML ソース\]** ウィンドウからワークシート内の対応するコントロールの作成場所に要素をドラッグします。  
  
     非繰り返しスキーマ要素をドラッグすると、Officeプロジェクトは <xref:System.Windows.Forms.BindingSource>に自動的にバインドされます <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> のコントロールを生成します。  
  
     繰り返しスキーマ要素をドラッグすると、Officeプロジェクトは自動的にデータ ソースにバインドされない <xref:Microsoft.Office.Tools.Excel.ListObject> のコントロールを生成します。  詳細については、「[ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)」を参照してください。  
  
## 参照  
 [方法 : Visual Studio 内で Word 文書にスキーマを割り当てる](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  