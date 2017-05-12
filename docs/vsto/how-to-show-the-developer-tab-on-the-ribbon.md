---
title: "方法 :タブをリボンに表示する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "[開発] タブ [Visual Studio での Office 開発]"
  - "リボン [Visual Studio での Office 開発], タブ"
ms.assetid: ce7cb641-44f2-4a40-867e-a7d88f8e98a9
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 方法 :タブをリボンに表示する
  Office アプリケーションのリボン内にある **\[開発\]** タブは既定では表示されないため、このタブにアクセスするには、このタブが表示されるように構成する必要があります。  たとえば、Word のドキュメント レベルのカスタマイズに <xref:Microsoft.Office.Tools.Word.GroupContentControl> を追加しようとする場合、このタブを表示する必要があります。  
  
> [!NOTE]  
>  このガイダンスは Office 2010 以降のアプリケーションのみに適用されます。  2007 Microsoft Office System でこのタブを表示する場合は、このトピックの次のバージョン「[方法 : \[開発\] タブをリボンに表示する](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx)」を参照してください。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Access には **\[開発\]** タブはありません。  
  
### \[開発\] タブを表示するには  
  
1.  このトピックでサポートされている Office アプリケーションのいずれかを起動します。  このトピックで前述されている「**対象:**」メモを参照してください。  
  
2.  **\[ファイル\]** タブの **\[オプション\]** をクリックします。  
  
     次の図に、Office 2010 内の **\[ファイル\]** タブと **\[オプション\]** ボタンを示します。  
  
     ![Outlook 2010 で [ファイル]、[オプション] を選択](../vsto/media/vsto-office-file-tab.png "Outlook 2010 で [ファイル]、[オプション] を選択")  
  
     次の図に、Office 2013 内の **\[ファイル\]** タブを示します。  
  
     ![Outlook 2013 の [File] (ファイル) タブ](../vsto/media/vsto-office2013-filetab.png "Outlook 2013 の [File] (ファイル) タブ")  
  
     次の図に、Office 2013 内の **\[オプション\]** ボタンを示します。  
  
     ![Outlook 2013 Preview の [Options] (オプション) ボタン](../vsto/media/vsto-office2013-optionsbutton.png "Outlook 2013 Preview の [Options] (オプション) ボタン")  
  
3.  *ApplicationName* の **\[オプション\]** ダイアログ ボックスで、**\[リボンのユーザー設定\]** をクリックします。  
  
     次の図に、Excel 2010 内の **\[オプション\]** ダイアログ ボックスと **\[リボンのユーザー設定\]** ボタンを示します。  このボタンの位置は、このトピックの上部付近の「対象」セクションに記載されている他のすべてのアプリケーションで同様です。  
  
     ![[リボンのユーザー設定] ボタン](../vsto/media/vsto-office2010-customizeribbonbutton.png "[リボンのユーザー設定] ボタン")  
  
4.  メイン タブの一覧で、**\[開発\]** チェック ボックスをオンにします。  
  
     次の図に、Word 2010 および  **内の [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]\[開発\]** チェック ボックスを示します。  このチェック ボックスの位置は、このトピックの上部付近の「対象」セクションに記載されている他のすべてのアプリケーションと同様です。  
  
     ![[Word のオプション] ダイアログの [開発] チェック ボックス](../vsto/media/vsto-office2010-developercheckbox.png "[Word のオプション] ダイアログの [開発] チェック ボックス")  
  
5.  **\[OK\]** をクリックして **\[オプション\]** ダイアログ ボックスを閉じます。  
  
## 参照  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)  
  
  