---
title: '方法: 組み込みタブをカスタマイズします。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 939c9c6d2d50e9feb6a50d9b49b84620d96a03cc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872223"
---
# <a name="how-to-customize-a-built-in-tab"></a>方法: 組み込みタブをカスタマイズします。
  組み込みタブには、グループやコントロールを追加できます。組み込みタブは、Microsoft Office アプリケーションのリボンに用意されているタブです。 たとえば、**データ**タブは、Excel の組み込みタブ。 カスタム グループを作成すると、そのグループはタブの最後に表示されますが、タブ上のどこにでも移動できます。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  組み込みタブにグループを追加することはできますが、組み込みタブから組み込みグループを削除することはできません。  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>組み込みタブにグループを追加するには  
  
1.  リボン コード ファイルを右クリックして**ソリューション エクスプ ローラー**、 をクリックし、**ビュー デザイナー**します。  
  
    > [!NOTE]  
    >  リボン コード ファイルが表示されない場合**ソリューション エクスプ ローラー**、追加する必要があります、**リボン項目**をプロジェクトにします。 「[方法:リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)します。  
  
2.  リボン デザイナーでの任意のタブを右クリックし、をクリックし、**プロパティ**します。  
  
3.  **プロパティ**ウィンドウで、展開、 **ControlId**プロパティ、および設定して、 **[controlidtype]** プロパティを**Office**します。  
  
4.  設定、 **OfficeId**プロパティを*制御 ID*の組み込みタブをカスタマイズするのです。  
  
     コントロール ID は、Microsoft Office アプリケーションに組み込まれているタブ、グループ、コントロールを一意に識別する名前です。  
  
     コントロール Id の一覧は、次を参照してください。 [Office 2010 ヘルプ ファイル。Office fluent ユーザー インターフェイスのコントロール id](http://go.microsoft.com/fwlink/?LinkID=181052)します。  
  
5.  **Office リボン コントロール**のタブ、**ツールボックス**グループをタブにドラッグします。  
  
    > [!NOTE]  
    >  組み込みグループは、デザイナーには表示されません。 組み込みタブを使用しているかどうかを判断する唯一の方法を確認するはそのため、 **ControlId**  タブのプロパティ。  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>組み込みタブ上でグループを配置するには  
  
1.  リボン デザイナーで、カスタム グループを選択します。  
  
2.  **プロパティ**ウィンドウで、展開、**位置**プロパティ。  
  
3.  設定、 **PositionType**プロパティを適切な値。  
  
    -   **BeforeOfficeId**指定の組み込みグループの前に、グループを配置します。  
  
    -   **AfterOfficeId**指定の組み込みグループの後、グループに配置します。  
  
4.  設定、 **OfficeId**プロパティを組み込みのグループのコントロール ID。  
  
     コントロール Id の一覧は、次を参照してください。 [Office 2010 ヘルプ ファイル。Office fluent ユーザー インターフェイスのコントロール id](http://go.microsoft.com/fwlink/?LinkID=181052)します。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: リボン XML を使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [方法: リボンのカスタマイズの概要します。](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: リボンのタブの位置を変更します。](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: Backstage ビューにコントロールを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [方法: アドイン ユーザー インターフェイス エラーを表示します。](../vsto/how-to-show-add-in-user-interface-errors.md)  
