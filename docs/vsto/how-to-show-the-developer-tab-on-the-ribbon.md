---
title: '方法: リボンの [開発] タブを表示します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c8346a1f23cc9aa02291aa994a0cea51b7810345
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906801"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>方法: リボンの [開発] タブを表示します。
  アクセスする、**開発者** タブ、Office アプリケーションのリボンで、既定で表示されないため、このタブを表示するように構成する必要があります。 たとえば、Word のドキュメント レベルのカスタマイズに <xref:Microsoft.Office.Tools.Word.GroupContentControl> を追加しようとする場合、このタブを表示する必要があります。  
  
> [!NOTE]  
>  このガイダンスは Office 2010 以降のアプリケーションのみに適用されます。 2007 Microsoft Office System のこのタブは表示する場合は、このトピックの次のバージョンを参照してください。[方法。リボンの [開発] タブを表示する](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)します。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  アクセスはありません、**開発者**タブ。  
  
## <a name="to-show-the-developer-tab"></a>[開発] タブを表示するには  
  
1.  このトピックでサポートされている Office アプリケーションのいずれかを起動します。 参照してください、**に適用されます:** このトピックの前に注意してください。  
  
2.  **ファイル** タブで、選択、**オプション**ボタンをクリックします。  
  
     次に示します、**ファイル** タブと**オプション**Office 2010 でボタンをクリックします。  
  
     ![Outlook 2010 ではオプションのファイルを選択するには、](../vsto/media/vsto-office-file-tab.png "オプション ファイルを選択すると、Outlook 2010")  
  
     次に示します、**ファイル**Office 2013 でのタブ。  
  
     ![Outlook 2013 で、[ファイル] タブ](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 の [ファイル] タブ")  
  
     次に示します、**オプション**Office 2013 でボタンをクリックします。  
  
     ![Outlook 2013 Preview の [オプション] ボタン](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview で [オプション] ボタン")  
  
3.  _ApplicationName_**オプション** ダイアログ ボックスで、選択、**リボンのカスタマイズ**ボタンをクリックします。  
  
     次に示します、**オプション** ダイアログ ボックスおよび**リボンのカスタマイズ**Excel 2010 でボタンをクリックします。 このボタンの位置は、このトピックの上部付近の「対象」セクションに記載されている他のすべてのアプリケーションで同様です。  
  
     ![リボン ボタン](../vsto/media/vsto-office2010-customizeribbonbutton.png "[リボンのカスタマイズ] ボタン")  
  
4.  メイン タブの一覧で選択、**開発者**チェック ボックスをオンします。  
  
     次に示します、**開発者**Word 2010 でのチェック ボックスと[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]します。 このチェック ボックスの位置は、このトピックの上部付近の「対象」セクションに記載されている他のすべてのアプリケーションと同様です。  
  
     ![Word のオプションダイアログ ボックスの [開発] チェック ボックス](../vsto/media/vsto-office2010-developercheckbox.png "Word のオプションダイアログ ボックスで [開発] チェック ボックス")  
  
5.  選択、 **OK**を閉じる ボタン、**オプション** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)  
