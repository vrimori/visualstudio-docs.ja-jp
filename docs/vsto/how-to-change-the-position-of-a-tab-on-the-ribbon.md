---
title: "方法: リボンのタブの位置を変更する |Microsoft ドキュメント"
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
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5016651a6cc4f1316536c22d555a65aaba64b788
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>方法: リボンのタブの位置を変更する
  使用して、リボンにカスタム タブの順序を変更することができます、**タブ コレクション エディター**です。 リボン上の組み込みタブの前後にカスタム タブを配置することができます。 組み込みタブは、Microsoft Office アプリケーションのリボンに用意されているタブです。 たとえば、**データ**タブは、Excel の組み込みタブです。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>リボンのタブの順序を変更するには  
  
1.  リボン コード ファイル (.vb または .cs ファイル) を選択**ソリューション エクスプ ローラー**です。  
  
2.  **ビュー**  メニューのをクリックして**デザイナー**です。  
  
3.  リボン デザイナーを右クリックし、をクリックして**プロパティ**です。  
  
4.  **プロパティ**ウィンドウで、**タブ**プロパティ、省略記号ボタンをクリックして (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイルデザイナー楕円"))。  
  
     **タブ コレクション エディター**が表示されます。  
  
5.  **タブ コレクション エディター**で、**メンバー**一覧で、移動しをクリックして、または下向きの矢印をタブ オーダーを変更するタブを選択します。  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>リボン上の組み込みタブの前後にタブを配置するには  
  
1.  リボン デザイナーでは、カスタム タブを選択します。  
  
2.  **プロパティ**ウィンドウで、展開、 **ControlId**プロパティ、いることを確認しの値、 **[controlidtype]**プロパティに設定されている**カスタム**.  
  
3.  **プロパティ**ウィンドウで、展開、**位置**プロパティです。  
  
4.  設定、 **PositionType**プロパティに適切な値。  
  
    -   **[Beforeofficeid]**指定の組み込みタブの前に、グループを配置します。  
  
    -   **AfterOfficeId**指定の組み込みタブの後、グループに配置します。  
  
5.  設定、 **OfficeId**プロパティを組み込みタブのコントロール ID。  
  
     コントロール Id の一覧は、次を参照してください。 [Office 2010 ヘルプ ファイル: Office Fluent ユーザー インターフェイスのコントロール Id](http://go.microsoft.com/fwlink/?LinkID=181052)です。  
  
## <a name="see-also"></a>参照  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  