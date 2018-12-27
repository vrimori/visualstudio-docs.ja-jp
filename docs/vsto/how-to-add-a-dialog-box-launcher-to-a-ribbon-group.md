---
title: '方法: リボン グループにダイアログ ボックス起動ツールを追加します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f6ec94b8fc170f195b00a6c093605860c97048ed
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648698"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>方法: リボン グループにダイアログ ボックス起動ツールを追加します。
  ダイアログ ボックス起動ツールは、リボン上の任意のグループに追加できます。 ダイアログ ボックス起動ツールは、グループ内にある小さなアイコンです。 ユーザーは、関連するダイアログ ボックスまたはグループに関連するその他のオプションを提供する作業ウィンドウを開くには、このアイコンをクリックします。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>リボン グループにダイアログ ボックス起動ツールを追加するには  
  
1.  リボン コード ファイルを選択します (*.vb*または *.cs*ファイル) で**ソリューション エクスプ ローラー**します。  
  
2.  **ビュー**  メニューのをクリックして**デザイナー**します。  
  
3.  リボン デザイナーで任意のグループを右クリックし をクリックし、**追加ダイアログ ボックス起動ツール**します。  
  
     コードを追加して、<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick>またはカスタムの組み込みダイアログ ボックスを開き、グループのイベント。  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [実行時にリボンへのアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [方法: XML をリボンをリボン デザイナーからエクスポートします。](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [方法: リボンのタブの位置を変更します。](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: Backstage ビューにコントロールを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Outlook のリボンをカスタマイズします。](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法: リボンのカスタマイズの概要します。](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [方法: アドイン ユーザー インターフェイス エラーを表示します。](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル: 実行時にリボン上のコントロールを更新します。](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [チュートリアル: リボン XML を使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  