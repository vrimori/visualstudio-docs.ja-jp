---
title: "方法 : Visual Studio 内で Word 文書にスキーマを割り当てる"
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
  - "マップ [Visual Studio での Office 開発], XML スキーマ (Word ドキュメントに)"
  - "Word [Visual Studio での Office 開発], マップ (XML スキーマを)"
  - "XML スキーマ [Visual Studio での Office 開発], マップ"
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法 : Visual Studio 内で Word 文書にスキーマを割り当てる
  **重要** は、マイクロソフトが米国カスタムにある場合や、実行用のプログラム、2010年1月1日の前のMicrosoftによってライセンスMicrosoft Word製品使用している個々の利点のためにMicrosoft Wordに関するこのトピックに記載されているMicrosoft情報がMicrosoft WordからカスタムXMLに関連する特定の機能の実装を削除したときに、使用、および組織。  ここに記載されている Microsoft Word に関する情報を、2010 年 1 月以降にマイクロソフトがライセンスを供与した Microsoft Word 製品上で実行されるプログラムを使用または開発する、米国およびその領土内の個人または組織が参照および使用することはお勧めしません。これに該当する製品は、この日付以前にライセンスが供与された製品、および米国外での使用を目的として購入またはライセンスが供与された製品と同様には動作しません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Visual Studio で文書を開いているときに、その文書に XML スキーマを割り当てることができます。  Visual Studio の外部で文書を開いているときに使用するのと同じ Microsoft Office Word ツールを使用します。  Word ソリューションを作成する前に文書にスキーマを割り当てるか、作成した後に割り当てるかにかかわらず、Office プロジェクトは同じオブジェクトを作成します。  
  
### Visual Studio 内で Word 文書に XML スキーマを割り当てるには  
  
1.  Visual Studio で、Word 文書またはテンプレート プロジェクトを開きます。  
  
2.  文書内をクリックしてデザイナーからフォーカスを移動します。  
  
3.  リボンの **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。  詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
4.  **\[XML\]** グループで、**\[スキーマ\]** をクリックします。  
  
     **\[テンプレートとアドイン\]** ダイアログ ボックスが表示されます。  
  
5.  **\[XML スキーマ\]** タブをクリックします。  
  
6.  **\[スキーマの追加\]** をクリックします。  
  
     **\[スキーマの追加\]** ダイアログ ボックスが表示されます。  
  
7.  目的のスキーマ ファイルに移動して選択し、**\[開く\]** をクリックします。  
  
     **\[スキーマの設定\]** ダイアログ ボックスが表示されます。  
  
8.  エイリアスを割り当てるか、**\[OK\]** をクリックしてエイリアスなしでスキーマを割り当てます。  
  
9. **\[OK\]** をクリックします。  
  
     **\[XML データ構造\]** ウィンドウが表示されます。  
  
10. **\[XML データ構造\]** ウィンドウから文書内の対応するコントロールの作成場所に要素をドラッグします。  
  
## 参照  
 [方法 : Visual Studio 内でワークシートにスキーマを割り当てる](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  