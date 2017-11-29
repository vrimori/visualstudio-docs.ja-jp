---
title: "方法: [開発] タブをリボンに表示 |Microsoft ドキュメント"
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
- Developer tab [Office development in Visual Studio]
ms.assetid: ce7cb641-44f2-4a40-867e-a7d88f8e98a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cad7fb4fe49df9688a0b9e7b3baa1f1108694136
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>方法 : [開発] タブをリボンに表示する
  アクセスする、**開発者**タブ Office アプリケーションのリボンの既定では表示されないので、そのタブを表示することを構成する必要があります。 たとえば、Word のドキュメント レベルのカスタマイズに <xref:Microsoft.Office.Tools.Word.GroupContentControl> を追加しようとする場合、このタブを表示する必要があります。  
  
> [!NOTE]  
>  このガイダンスは Office 2010 以降のアプリケーションのみに適用されます。 2007 Microsoft Office System でこのタブは表示するには、このトピックの次のバージョンを参照して[する方法: [開発] タブをリボンに表示](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx)です。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  アクセスがない、**開発者**タブです。  
  
### <a name="to-show-the-developer-tab"></a>[開発] タブを表示するには  
  
1.  このトピックでサポートされている Office アプリケーションのいずれかを起動します。 参照してください、**に適用されます:**このトピックの前半には、注意してください。  
  
2.  **ファイル** タブで、選択、**オプション**ボタンをクリックします。  
  
     次の図に示しています、**ファイル** タブと**オプション**Office 2010 でボタンをクリックします。  
  
     ![Outlook 2010 ではオプションのファイルを選択すると、](../vsto/media/vsto-office-file-tab.png "ファイルを選択すると、Outlook 2010 でのオプション")  
  
     次の図に示しています、**ファイル**Office 2013 内のタブです。  
  
     ![Outlook 2013 で、[ファイル] タブ](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 で [ファイル] タブ")  
  
     次の図に示しています、**オプション**Office 2013 でボタンをクリックします。  
  
     ![Outlook 2013 Preview で [オプション] ボタン](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview で [オプション] ボタン")  
  
3.  *ApplicationName***オプション** ダイアログ ボックスで、選択、**リボンのカスタマイズ**ボタンをクリックします。  
  
     次に示します、**オプション** ダイアログ ボックスおよび**リボンのカスタマイズ**Excel 2010 でボタンをクリックします。 このボタンの位置は、このトピックの上部付近の「対象」セクションに記載されている他のすべてのアプリケーションで同様です。  
  
     ![リボンのカスタマイズ ボタン](../vsto/media/vsto-office2010-customizeribbonbutton.png "[リボンのカスタマイズ] ボタン")  
  
4.  メイン タブの一覧で選択、**開発者**チェック ボックスをオンします。  
  
     次の図に示しています、**開発者**Word 2010 でのチェック ボックスと[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]です。 このチェック ボックスの位置は、このトピックの上部付近の「対象」セクションに記載されている他のすべてのアプリケーションと同様です。  
  
     ![Word のオプション ダイアログ ボックスの [開発] チェック ボックス](../vsto/media/vsto-office2010-developercheckbox.png "Word のオプション ダイアログ ボックスで [開発者] チェック ボックス")  
  
5.  選択、 **OK**を閉じる ボタン、**オプション** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)  
  
  