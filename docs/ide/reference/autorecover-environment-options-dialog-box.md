---
title: '[自動バックアップ]\ ([オプション] ダイアログ ボックス - [環境])'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed5ad6259ede32304cfe15ef4e79c6b3e56dbd9d
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143308"
---
# <a name="autorecover-environment-options-dialog-box"></a>[自動バックアップ]\ ([オプション] ダイアログ ボックス - [環境])

**[オプション]** ダイアログ ボックスのこのページを使用し、ファイルを自動的にバックアップするかどうかを指定します。 このページでは、Visual Studio が突然終了した場合に、変更したファイルを復元するかどうかを指定することもできます。

このダイアログ ボックスにアクセスするには、**[ツール]** メニューを選択し、**[オプション]** を選択して、**[環境]** > **[自動バックアップ]** を選択します。 このページが一覧に表示されない場合は、**[オプション]** ダイアログ ボックスの **[すべての設定を表示]** を選択します。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

**自動バックアップの実行間隔: [n] 分**

このオプションを使用し、エディターでファイルを自動的に保存する頻度をカスタマイズします。 以前に保存したファイルに関しては、ファイルのコピーは *%USERPROFILE%\Documents\Visual Studio \<version>\Backup Files\\<projectname>* に保存されています。 ファイルが新しく、手動でまだ保存していない場合、ファイルはランダムに生成されたファイル名で自動保存されます。

**自動バックアップした情報の保存期間: [n] 日**

このオプションを使用し、Visual Studio で自動バックアップのために作成したファイルを保存する期間を指定します。

## <a name="see-also"></a>関連項目

- [[オプション] ダイアログ ボックス](../../ide/reference/options-dialog-box-visual-studio.md)