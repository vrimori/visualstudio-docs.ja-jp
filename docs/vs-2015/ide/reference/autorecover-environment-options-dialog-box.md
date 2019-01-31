---
title: '[自動バックアップ] ([オプション] ダイアログ ボックス - [環境]) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e5fc9c1d835979c53b499e88e3949d5023e077e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766074"
---
# <a name="autorecover-environment-options-dialog-box"></a>[自動バックアップ]\ ([オプション] ダイアログ ボックス - [環境])
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[オプション] ダイアログ ボックスのこのページを使用し、ファイルを自動的にバックアップするかどうかを指定します。 このページではまた、IDE (統合開発環境) が突然シャットダウンしたとき、変更済みのファイルを復元するかどうかも指定できます。 このダイアログ ボックスにアクセスするには、**[ツール]** メニューを選択し、**[オプション]** を選択し、**[環境]** フォルダーを選択し、**[自動バックアップ]** ページを選択します。 このページが一覧に表示されない場合は、**[オプション]** ダイアログ ボックスの **[すべての設定を表示]** を選択します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **自動バックアップの実行間隔: \<n> 分**  
 このオプションを使用し、エディターでファイルを自動的に保存する頻度をカスタマイズします。 以前に保存したファイルに関しては、ファイルのコピーは \\...\My Documents\Visual Studio \<*version*>\Backup Files\\<*projectname*> に保存されています。 ファイルが新しく、手動で保存されていない場合、ファイルはランダムに生成されたファイル名で自動保存されます。  
  
 **自動バックアップした情報の保存期間: \<n> 日**  
 このオプションを使用し、Visual Studio で自動バックアップのために作成したファイルを保存する期間を指定します。  
  
## <a name="see-also"></a>関連項目  
 [[オプション] ダイアログ ボックス](../../ide/reference/options-dialog-box-visual-studio.md)
