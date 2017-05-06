---
title: "方法 : Word 文書に XMLNode コントロールを追加する"
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
  - "XMLNode コントロール, 追加 (ドキュメントに)"
ms.assetid: d583b9d4-bd13-46e3-9eb7-da18fcb7eb8c
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 方法 : Word 文書に XMLNode コントロールを追加する
  **重要** は、マイクロソフトが米国カスタムにある場合や、実行用のプログラム、2010年1月1日の前のMicrosoftによってライセンスMicrosoft Word製品使用している個々の利点のためにMicrosoft Wordに関するこのトピックに記載されているMicrosoft情報がMicrosoft WordからカスタムXMLに関連する特定の機能の実装を削除したときに、使用、および組織。  ここに記載されている Microsoft Word に関する情報を、2010 年 1 月以降にマイクロソフトがライセンスを供与した Microsoft Word 製品上で実行されるプログラムを使用または開発する、米国およびその領土内の個人または組織が参照および使用することはお勧めしません。これに該当する製品は、この日付以前にライセンスが供与された製品、および米国外での使用を目的として購入またはライセンスが供与された製品と同様には動作しません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 非繰り返し XML スキーマ要素を Microsoft Office Word 文書にマップすると、Visual Studio によって <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールが文書に自動的に追加されます。  繰り返し XML スキーマ要素のマップの詳細については、「[方法 : Word 文書に XMLNodes コントロールを追加する](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)」を参照してください。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールは、**ツールボックス**または **\[データ ソース\]** ウィンドウから利用することはできず、プログラムによって作成することもできません。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 文書に XMLNode コントロールを追加するには  
  
1.  Visual Studio デザイナーの文書のリボンで **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。  詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
2.  **\[XML\]** グループで、**\[スキーマ\]** をクリックします。  
  
     **\[テンプレートとアドイン\]** ダイアログ ボックスが表示されます。  
  
3.  **\[XML スキーマ\]** タブをクリックします。  
  
4.  **\[スキーマの追加\]** をクリックします。  
  
     **\[スキーマの追加\]** ダイアログ ボックスが表示されます。  
  
5.  **\[スキーマの追加\]** ダイアログ ボックスで非繰り返しスキーマ要素を含んだ XML スキーマを選択し、**\[開く\]** をクリックします。  
  
     **\[スキーマの設定\]** ダイアログ ボックスが表示されます。  
  
6.  エイリアスを割り当てるか、**\[OK\]** をクリックしてエイリアスなしでスキーマを割り当てます。  
  
     **\[スキーマの追加\]** ダイアログ ボックスにスキーマが追加されます。  
  
7.  **\[スキーマの追加\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
8.  **\[XML データ構造\]** 作業ウィンドウが表示されます。  
  
9. **\[XML データ構造\]** 作業ウィンドウで非繰り返しスキーマ要素をクリックして文書に追加します。  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode> コントロールが作成され、プロジェクトに追加されます。  
  
## 参照  
 [XMLNode コントロール](../vsto/xmlnode-control.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  