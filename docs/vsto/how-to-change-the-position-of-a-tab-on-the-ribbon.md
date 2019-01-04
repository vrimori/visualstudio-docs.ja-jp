---
title: '方法: リボンのタブの位置を変更します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f1b324ec6e43639b55ba308aab7028592c8671d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956517"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>方法: リボンのタブの位置を変更します。
  使用して、リボンのカスタム タブの順序を変更することができます、**タブ コレクション エディター**します。 リボン上の組み込みタブの前後には、カスタム タブを配置することができます。 組み込みタブは、Microsoft Office アプリケーションのリボンに用意されているタブです。 たとえば、**データ**タブは、Excel の組み込みタブ。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>リボンのタブの順序を変更するには  
  
1.  リボン コード ファイルを選択します (*.vb*または *.cs*ファイル) で**ソリューション エクスプ ローラー**します。  
  
2.  **ビュー**  メニューのをクリックして**デザイナー**します。  
  
3.  リボン デザイナーを右クリックし、をクリックし、**プロパティ**します。  
  
4.  **プロパティ**ウィンドウで、**タブ**プロパティ、省略記号ボタンをクリックし、(![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイルデザイナー楕円"))。  
  
     **タブ コレクション エディター**が表示されます。  
  
5.  **タブ コレクション エディター**の**メンバー**一覧で、移動またはをクリックし、下向きの矢印をタブ オーダーを変更するタブを選択します。  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>リボン上の組み込みタブの前後にタブを配置するには  
  
1.  リボン デザイナーでは、カスタム タブを選択します。  
  
2.  **プロパティ**ウィンドウで、展開、 **ControlId**プロパティ、いることを確認しの値、 **[controlidtype]** プロパティに設定されて**カスタム**.  
  
3.  **プロパティ**ウィンドウで、展開、**位置**プロパティ。  
  
4.  設定、 **PositionType**プロパティを適切な値。  
  
    -   **BeforeOfficeId**組み込みタブを指定する前に、グループを配置します。  
  
    -   **AfterOfficeId**指定の組み込みタブの後、グループに配置します。  
  
5.  設定、 **OfficeId**プロパティを組み込みタブのコントロール ID。  
  
     コントロール Id の一覧は、次を参照してください。 [Office 2010 ヘルプ ファイル。Office fluent ユーザー インターフェイスのコントロール id](http://go.microsoft.com/fwlink/?LinkID=181052)します。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: リボン XML を使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
