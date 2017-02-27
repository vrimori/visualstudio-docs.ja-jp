---
title: "[自動バックアップ] ([オプション] ダイアログ ボックス - [環境]) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPag.Environment.AutoRecover"
  - "VS.DialogAutoRestore"
  - "VS.ToolsOptionsPages.Environment.AutoRecover"
  - "VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore"
helpviewer_keywords: 
  - "ファイル、復元"
  - "[自動バックアップ] ページ"
  - "ファイルの保存、自動"
  - "ファイル、自動的に保存"
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# [自動バックアップ] ([オプション] ダイアログ ボックス - [環境])
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[オプション\] ダイアログ ボックスのこのページを使用すると、ファイルを自動的にバックアップするかどうかを指定できます。  このぺージでは、統合開発環境 \(IDE: Integrated Development Environment\) が予期せず終了した場合に、変更されたファイルを復元するかどうかを指定することもできます。  このダイアログ ボックスを表示するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。次に、**\[環境\]** フォルダーを選択し、**\[自動バックアップ\]** ページを選択します。  このページが一覧に表示されない場合は、**\[オプション\]** ダイアログ ボックスの **\[すべての設定を表示\]** を選択します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、\[ツール\] メニューの \[設定のインポートとエクスポート\] をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **\[自動バックアップ情報を \<n\> 分毎に保存します。\]**  
 このオプションを使用すると、エディター内でファイルを自動的に保存する頻度をカスタマイズできます。  以前に保存されたファイルについては、ファイルのコピーが、\\...  \\My Documents\\Visual Studio \<*version*\>\\Backup Files\\\<*projectname*\> に保存されます。  ファイルが新規であり、今まで一度も手動で保存されていない場合は、ランダムに生成されたファイル名で自動的に保存されます。  
  
 **\[自動バックアップした情報の保存期間 \<n\> 日\]**  
 このオプションを使用すると、自動バックアップで作成されたファイルを Visual Studio で保存する期間を指定できます。  
  
## 参照  
 [\[オプション\] ダイアログ ボックス](../Topic/Options%20Dialog%20Box%20\(Visual%20Studio\).md)