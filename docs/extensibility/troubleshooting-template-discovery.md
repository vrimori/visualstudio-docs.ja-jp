---
title: "Visual Studio でテンプレートの検出のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 72663d56844fcc34164e9408ab14c8ead234683e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="troubleshooting-template-installation"></a>テンプレートのインストールのトラブルシューティング

問題は、プロジェクトまたは項目テンプレートの展開に実行する場合は、診断ログの記録を有効にできます。

1. 次の内容の pkgdef ファイル Common7\IDE\CommonExtensions フォルダーにインストール (例: C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) を作成します。

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. 「開発者コマンド プロンプト」、インストールして Windows search に探して開き実行`devenv /updateConfiguration`です。

1. Visual Studio を起動し、両方のテンプレート ツリーを初期化するために、新しいプロジェクトと新しい項目の追加ダイアログ ボックスを起動します。 テンプレートは、ログに表示されるよう**%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid は Visual Studio のインスタンスのインストール ID に相当します)。 各テンプレート ツリー初期化は、このログにエントリを追加します。

ログ ファイルには、次の列が含まれています。

- **FullPathToTemplate**、次の値を持ちます。

    - マニフェスト ベースの展開の場合は 1

    - ディスク ベースの展開の場合は 0

- **TemplateFileName**

- その他のテンプレートのプロパティ

> [!NOTE]
> ログ記録を無効にするには、pkgdef ファイルを削除するかの値を変更`EnableTemplateDiscoveryLog`に`dword:00000000`、し、実行`devenv /updateConfiguration`もう一度です。

## <a name="see-also"></a>関連項目

[カスタム プロジェクトと項目テンプレートを作成します。](creating-custom-project-and-item-templates.md)