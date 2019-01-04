---
title: Visual Studio でテンプレート検出のトラブルシューティング |Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39ebb7c49e5a8482ab0b2ef5c3a5257d0237b39c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836154"
---
# <a name="troubleshooting-template-installation"></a>テンプレートのインストールのトラブルシューティング

プロジェクトまたは項目テンプレートのデプロイ時に問題が発生した場合は、診断ログを有効にできます。

1. 次の内容の Common7\IDE\CommonExtensions フォルダー (例: C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) インストールの pkgdef ファイルを作成します。

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Windows search の検索、インストールに"Developer Command Prompt"を開くし、実行`devenv /updateConfiguration`します。

1. Visual Studio を起動し、両方のテンプレートのツリーを初期化するために、新しいプロジェクトと新しい項目のダイアログ ボックスを起動します。 テンプレートは、ログに表示されている **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (インスタンス id は、Visual Studio のインスタンスのインストール ID に対応)。 各テンプレート ツリーの初期化では、このログにエントリを追加します。

ログ ファイルには、次の列が含まれています。

- **FullPathToTemplate**、次の値を持ちます。

    - マニフェスト ベースの展開 1

    - ディスク ベースの展開の場合は 0

- **TemplateFileName**

- その他のテンプレートのプロパティ

> [!NOTE]
> ログ記録を無効にするか、pkgdef ファイルを削除またはの値を変更`EnableTemplateDiscoveryLog`に`dword:00000000`、し、実行`devenv /updateConfiguration`もう一度です。

## <a name="see-also"></a>関連項目

[カスタム プロジェクトと項目テンプレートの作成](creating-custom-project-and-item-templates.md)