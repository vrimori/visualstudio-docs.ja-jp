---
title: "方法: 組み込みタブをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 08b20f308e4022b7ad12d68a92f7cb5422728639
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-built-in-tab"></a>方法 : 組み込みタブをカスタマイズする
  組み込みタブには、グループやコントロールを追加できます。組み込みタブは、Microsoft Office アプリケーションのリボンに用意されているタブです。 たとえば、**データ**タブは、Excel の組み込みタブです。 カスタム グループを作成すると、そのグループはタブの最後に表示されますが、タブ上のどこにでも移動できます。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  組み込みタブにグループを追加することはできますが、組み込みタブから組み込みグループを削除することはできません。  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>組み込みタブにグループを追加するには  
  
1.  リボン コード ファイルを右クリックして**ソリューション エクスプ ローラー**、クリックして**ビュー デザイナー**です。  
  
    > [!NOTE]  
    >  リボン コード ファイルが表示されない場合**ソリューション エクスプ ローラー**、追加する必要があります、**リボン項目**をプロジェクトにします。 参照してください[する方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)です。  
  
2.  リボン デザイナーで、任意のタブを右クリックし、をクリックして**プロパティ**です。  
  
3.  **プロパティ**ウィンドウで、展開、 **ControlId**プロパティ、および設定、 **[controlidtype]**プロパティを**Office**です。  
  
4.  設定、 **OfficeId**プロパティを*制御 ID*をカスタマイズする組み込みタブです。  
  
     コントロール ID は、Microsoft Office アプリケーションに組み込まれているタブ、グループ、コントロールを一意に識別する名前です。  
  
     コントロール Id の一覧は、次を参照してください。 [Office 2010 ヘルプ ファイル: Office Fluent ユーザー インターフェイスのコントロール Id](http://go.microsoft.com/fwlink/?LinkID=181052)です。  
  
5.  **Office リボン コントロール**のタブ、**ツールボックス**、タブにグループをドラッグします。  
  
    > [!NOTE]  
    >  組み込みグループは、デザイナーには表示されません。 したがって、組み込みタブで動作しているかどうかを判別する唯一の方法を調べるには、 **ControlId**  タブのプロパティです。  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>組み込みタブ上でグループを配置するには  
  
1.  リボン デザイナーで、カスタム グループを選択します。  
  
2.  **プロパティ**ウィンドウで、展開、**位置**プロパティです。  
  
3.  設定、 **PositionType**プロパティに適切な値。  
  
    -   **[Beforeofficeid]**指定の組み込みグループの前に、グループを配置します。  
  
    -   **AfterOfficeId**指定の組み込みグループの後、グループに配置します。  
  
4.  設定、 **OfficeId**プロパティを組み込みのグループのコントロール ID。  
  
     コントロール Id の一覧は、次を参照してください。 [Office 2010 ヘルプ ファイル: Office Fluent ユーザー インターフェイスのコントロール Id](http://go.microsoft.com/fwlink/?LinkID=181052)です。  
  
## <a name="see-also"></a>参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: コントロール Backstage ビューを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [方法: アドインのユーザー インターフェイス エラーを表示する](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  