---
title: "方法 : Word 文書に XMLNodes コントロールを追加する | Microsoft Docs"
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
  - "コントロール [Visual Studio での Office 開発], 追加 (ドキュメントに)"
  - "XMLNodes コントロール, 追加 (ドキュメントに)"
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 方法 : Word 文書に XMLNodes コントロールを追加する
  **重要** は、マイクロソフトが米国カスタムにある場合や、実行用のプログラム、2010年1月1日の前のMicrosoftによってライセンスMicrosoft Word製品使用している個々の利点のためにMicrosoft Wordに関するこのトピックに記載されているMicrosoft情報がMicrosoft WordからカスタムXMLに関連する特定の機能の実装を削除したときに、使用、および組織。  ここに記載されている Microsoft Word に関する情報を、2010 年 1 月以降にマイクロソフトがライセンスを供与した Microsoft Word 製品上で実行されるプログラムを使用または開発する、米国およびその領土内の個人または組織が参照および使用することはお勧めしません。これに該当する製品は、この日付以前にライセンスが供与された製品、および米国外での使用を目的として購入またはライセンスが供与された製品と同様には動作しません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 繰り返し XML スキーマ要素を Microsoft Office Word 文書にマップすると、Visual Studio によって <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールが文書に自動的に追加されます。  
  
 非繰り返し XML スキーマ要素のマップの詳細については、「[方法 : Word 文書に XMLNode コントロールを追加する](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)」を参照してください。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールは、**ツールボックス**や **\[データ ソース\]** ウィンドウからは使用できません。また、プログラムで作成することもできません。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 文書に XMLNodes コントロールを追加するには  
  
1.  Visual Studio デザイナーの文書のリボンで **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。  詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
2.  **\[XML\]** グループで、**\[スキーマ\]** をクリックします。  
  
     **\[テンプレートとアドイン\]** ダイアログ ボックスが表示されます。  
  
3.  **\[XML スキーマ\]** タブをクリックします。  
  
4.  **\[スキーマの追加\]** をクリックします。  
  
     **\[スキーマの追加\]** ダイアログ ボックスが表示されます。  
  
5.  繰り返しスキーマ要素を含む XML スキーマを選択して **\[開く\]** をクリックします。  
  
     **\[スキーマの設定\]** ダイアログ ボックスが表示されます。  
  
6.  エイリアスを割り当てるか、**\[OK\]** をクリックしてエイリアスなしでスキーマを割り当てます。  
  
     **\[スキーマの追加\]** ダイアログ ボックスにスキーマが追加されます。  
  
7.  **\[スキーマの追加\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
     **\[XML データ構造\]** 作業ウィンドウが表示されます。  
  
8.  **\[XML データ構造\]** 作業ウィンドウの繰り返しスキーマ要素をクリックして文書に追加します。  
  
     <xref:Microsoft.Office.Tools.Word.XMLNodes> コントロールが作成され、プロジェクトに追加されます。  
  
## 参照  
 [XMLNodes コントロール](../vsto/xmlnodes-control.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  