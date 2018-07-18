---
title: Visual Studio でテンプレートの検出のトラブルシューティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d183fd664258fbb7dbcf27c913c56c6f6160e6c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136729"
---
# <a name="troubleshooting-template-installation"></a>テンプレートのインストールのトラブルシューティング

問題は、プロジェクトまたは項目テンプレートの展開に実行する場合は、診断ログの記録を有効にできます。

1. 次の内容の pkgdef ファイル Common7\IDE\CommonExtensions フォルダーにインストール (例: C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) を作成します。

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. 「開発者コマンド プロンプト」、インストールして Windows search に探して開き実行`devenv /updateConfiguration`です。

1. Visual Studio を起動し、両方のテンプレート ツリーを初期化するために、新しいプロジェクトと新しい項目の追加ダイアログ ボックスを起動します。 テンプレートは、ログに表示されるよう **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid は Visual Studio のインスタンスのインストール ID に相当します)。 各テンプレート ツリー初期化は、このログにエントリを追加します。

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