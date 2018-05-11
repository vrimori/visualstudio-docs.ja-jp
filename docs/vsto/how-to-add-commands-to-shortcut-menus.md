---
title: '方法: ショートカット メニューにコマンドを追加 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0d1bf0aee988e194b51220588a710a4b5b8d66ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>方法: ショートカット メニューにコマンドを追加する
  このトピックでは、VSTO アドインを使用して、Office アプリケーションのショートカット メニューにコマンドを追加する方法を示します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Office のショートカット メニューにコマンドを追加するには  
  
1.  **[リボン XML]** 項目をドキュメント レベルのプロジェクトまたは VSTO アドイン プロジェクトに追加します。 詳細については、「 [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)」を参照してください。 イン  
  
2.  **ソリューション エクスプローラー**で、 **ThisAddin.cs** または **ThisAddin.vb**を選択します。  
  
3.  メニュー バーで **[表示]**、 **[コード]**の順に選択します。  
  
     コード エディターで **ThisAddin** クラス ファイルが開きます。  
  
4.  次のコードを **ThisAddin** クラスに追加します。 このコードは、CreateRibbonExtensibilityObject メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  **[ソリューション エクスプローラー]**でリボン XML ファイルを選択します。 既定では、リボン XML ファイルには Ribbon1.xml という名前が付けられます。  
  
6.  メニュー バーで **[表示]**、 **[コード]**の順に選択します。  
  
     コード エディターでリボン XML ファイルが開きます。  
  
7.  コード エディターで、ショートカット メニューとショートカット メニューに追加するコントロールを記述する XML を追加します。  
  
     次の例では、ボタン、メニュー、および Gallery コントロールを Word ドキュメントのショートカット メニューに追加します。 このショートカット メニューのコントロール ID は、ContextMenuText です。 Office 2010 ショートカットのコントロールの完全な一覧については、ID を参照してください[Office 2010 ヘルプ ファイル: Office Fluent ユーザー インターフェイスのコントロール Id](http://go.microsoft.com/fwlink/?LinkID=181052)です。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  **ソリューション エクスプローラー**で、 **MyRibbon.cs** または **MyRibbon.vb**を選択します。  
  
9. 処理する各コントロールの `Ribbon1` クラスに、コールバック メソッドを追加します。  
  
     次のコールバック メソッドは、 **[My Button]** ボタンを処理します。 このコードは、アクティブ ドキュメントの現在のカーソル位置に文字列を追加します。  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>関連項目  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [チュートリアル: ブックマークのショートカット メニューを作成します。](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Office 2010 のコンテキスト メニューのカスタマイズ](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  