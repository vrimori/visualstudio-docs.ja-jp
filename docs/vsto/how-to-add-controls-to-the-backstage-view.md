---
title: '方法: コントロール、Backstage ビューを追加します。 '
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d72cd3371a1465faa1dd505f71c5fe8c9e2e181d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>方法: コントロール、Backstage ビューを追加します。
  リボン デザイナーを使用するには、をクリックしたときに表示されるメニューにコントロールを追加、**ファイル**タブ コントロールに追加するアプリケーションを実行するときに、**ファイル** タブに表示されるという名前のグループ**アドイン**です。  
  
 Visual Studio でリボン デザイナーを使用して、組み込みのコントロールの前後にコントロールを配置できません。 ビルトイン コントロールは、Backstage ビューで既に表示されているコントロールです。 組み込みコントロールの前後にコントロールを配置する場合は、リボン XML を使用する必要があります。 詳細については**リボン (XML)** を参照してください[リボン XML](../vsto/ribbon-xml.md)です。 Backstage ビューのカスタマイズの詳細については、次を参照してください。[開発者向けの Office 2010 の Backstage ビューの概要](http://go.microsoft.com/fwlink/?LinkId=182189)と[開発者向けの Office 2010 の Backstage ビューをカスタマイズ](http://go.microsoft.com/fwlink/?LinkId=182188)です。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Backstage ビューにコントロールを追加するには  
  
1.  デザイン ビューで、リボン項目を開きます。  
  
     追加する方法については、**リボン (ビジュアル デザイナー)** をプロジェクトに項目を参照してください[する方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)です。  
  
2.  リボン デザイナーで、をクリックして、**ファイル**タブです。  
  
     メニューのデザイナーが表示されます。 このデザイン サーフェイスにコントロールが含まれていません。  
  
3.  **Office リボン コントロール**のタブ、**ツールボックス**、次のコントロールのメニュー デザイナーにドラッグします。  
  
    -   ボタン  
  
    -   CheckBox  
  
    -   Gallery  
  
    -   メニュー  
  
    -   区切り記号  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  メニューの新しい位置に移動するコントロールをドラッグします。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  