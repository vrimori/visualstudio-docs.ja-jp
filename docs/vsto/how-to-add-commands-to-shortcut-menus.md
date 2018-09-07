---
title: '方法: ショートカット メニュー コマンドを追加'
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
ms.openlocfilehash: 9accca69c5d56461f07d21d25821c0f4181c8fbd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672675"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>方法: ショートカット メニュー コマンドを追加
  このトピックでは、VSTO アドインを使用して Office アプリケーションのショートカット メニューにコマンドを追加する方法を示します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Office のショートカット メニューにコマンドを追加するには  
  
1.  **[リボン XML]** 項目をドキュメント レベルのプロジェクトまたは VSTO アドイン プロジェクトに追加します。 詳細については、次を参照してください。[方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)します。 イン  
  
2.  **ソリューション エクスプローラー**で、 **ThisAddin.cs** または **ThisAddin.vb**を選択します。  
  
3.  メニュー バーで **[表示]** > **[コード]** の順に選択します。  
  
     コード エディターで **ThisAddin** クラス ファイルが開きます。  
  
4.  次のコードを **ThisAddin** クラスに追加します。 このコードは、`CreateRibbonExtensibilityObject` メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  **[ソリューション エクスプローラー]** でリボン XML ファイルを選択します。 既定では、リボン XML ファイルの名前は*Ribbon1.xml*します。  
  
6.  メニュー バーで **[表示]** > **[コード]** の順に選択します。  
  
     コード エディターでリボン XML ファイルが開きます。  
  
7.  コード エディターで、ショートカット メニューとショートカット メニューに追加するコントロールを記述する XML を追加します。  
  
     次の例では、ボタン、メニュー、および Gallery コントロールを Word ドキュメントのショートカット メニューに追加します。 このショートカット メニューのコントロール ID は、ContextMenuText です。 Office 2010 ショートカットのコントロールの完全な一覧については、ID を参照してください[Office 2010 ヘルプ ファイル: Office fluent ユーザー インターフェイスのコントロール id](http://go.microsoft.com/fwlink/?LinkID=181052)します。  
  
    ```xml
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
  
9. コールバック メソッドを追加、`Ribbon1`を処理する各コントロールのクラス。  
  
     次のコールバック メソッドは、 **[My Button]** ボタンを処理します。 このコードは、アクティブ ドキュメントの現在のカーソル位置に文字列を追加します。  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>関連項目  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [チュートリアル: ブックマークのショートカット メニューを作成します。](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Office 2010 でのコンテキスト メニューをカスタマイズします。](http://go.microsoft.com/fwlink/?LinkId=182186)  
  