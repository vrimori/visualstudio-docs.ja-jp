---
title: "方法: ショートカット メニューにコマンドを追加する | Microsoft Docs"
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
  - "Office メニュー、作成"
  - "Visual Studio での Office 開発、コンテキスト メニュー"
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法: ショートカット メニューにコマンドを追加する
  このトピックでは、VSTO アドインを使用して、Office アプリケーションのショートカット メニューにコマンドを追加する方法を示します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### Office のショートカット メニューにコマンドを追加するには  
  
1.  **\[リボン XML\]** 項目をドキュメント レベルのプロジェクトまたは VSTO アドイン プロジェクトに追加します。 詳細については、「[方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)」を参照してください。 イン  
  
2.  **ソリューション エクスプローラー**で、**ThisAddin.cs** または **ThisAddin.vb** を選択します。  
  
3.  メニュー バーで **\[表示\]**、**\[コード\]** の順に選択します。  
  
     コード エディターで **ThisAddin** クラス ファイルが開きます。  
  
4.  次のコードを **ThisAddin** クラスに追加します。 このコードは、CreateRibbonExtensibilityObject メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/thisaddin.vb#1)]  
  
5.  **\[ソリューション エクスプローラー\]** でリボン XML ファイルを選択します。 既定では、リボン XML ファイルには Ribbon1.xml という名前が付けられます。  
  
6.  メニュー バーで **\[表示\]**、**\[コード\]** の順に選択します。  
  
     コード エディターでリボン XML ファイルが開きます。  
  
7.  コード エディターで、ショートカット メニューとショートカット メニューに追加するコントロールを記述する XML を追加します。  
  
     次の例では、ボタン、メニュー、および Gallery コントロールを Word ドキュメントのショートカット メニューに追加します。 このショートカット メニューのコントロール ID は、ContextMenuText です。 Office 2010 ショートカットのコントロール ID の完全な一覧については、「[Office 2010 ヘルプ ファイル: Office Fluent ユーザー インターフェイスのコントロール ID](http://go.microsoft.com/fwlink/?LinkID=181052)」を参照してください。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui"> <contextMenus> <contextMenu idMso="ContextMenuText"> <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" /> <menu id="MySubMenu" label="My Submenu" > <button id="MyButton2" label="Button on submenu" /> </menu> <gallery id="galleryOne" label="My Gallery"> <item id="item1" imageMso="HappyFace" /> <item id="item2" imageMso="HappyFace" /> <item id="item3" imageMso="HappyFace" /> <item id="item4" imageMso="HappyFace" /> </gallery> </contextMenu> </contextMenus> </customUI>  
    ```  
  
8.  **ソリューション エクスプローラー** で、**MyRibbon.cs** または **MyRibbon.vb** を選択します。  
  
9. 処理する各コントロールの `Ribbon1` クラスに、コールバック メソッドを追加します。  
  
     次のコールバック メソッドは、**\[My Button\]** ボタンを処理します。 このコードは、アクティブ ドキュメントの現在のカーソル位置に文字列を追加します。  
  
     [!code-csharp[Trin_WordAddIn_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/ribbon1.cs#2)]
     [!code-vb[Trin_WordAddIn_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/ribbon1.vb#2)]  
  
## 参照  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [チュートリアル : ブックマークのショートカット メニューの作成](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Office 2010 のコンテキスト メニューのカスタマイズ](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  