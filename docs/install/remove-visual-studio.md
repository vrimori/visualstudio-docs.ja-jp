---
title: Visual Studio の削除
titleSuffix: ''
description: コンピューターから Visual Studio を完全に削除する詳細な手順を説明します。
ms.date: 09/12/2017
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26d29ccf0bfa834ec7581fea11a606ce0558cf74
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985668"
---
# <a name="remove-visual-studio-2017"></a>Visual Studio 2017 の削除

致命的なエラーが発生して Visual Studio の修復またはアンインストールができない場合は、`InstallCleanup.exe` ツールを実行して Visual Studio 2017 以降のすべてのインストール済みインスタンスのインストール ファイルと製品情報を削除することができます。 このツールの実行は修復またはアンインストールに失敗した場合の最終手段として行ってください。その他の Visual Studio のインストールやその他の製品の機能がアンインストールされ、後で修復が必要になる場合があります。

以下の手順では、以下の動作のコマンドライン スイッチでツールを実行することができます。

| 切り替え | 動作 |
| ------ | -------- |
| `-i`   | その他のスイッチが渡されていない場合、このスイッチが既定で、メインのインストール ディレクトリと製品情報のみが削除されます。 `InstallCleanup.exe` ツールを実行した後に同じバージョンを再インストールする予定がある場合は、この動作が適しています。 |
| `-f`   | このスイッチを指定すると、メインのインストール ディレクトリ、製品情報、そして他の Visual Studio のインストールまたは他の製品と共有できるインストール ディレクトリ外にインストールされているその他の多くの機能が削除されます。 この動作は、後で再インストールせずに Visual Studio を削除する場合に適しています。 |

1. Visual Studio インストーラーを閉じます。
2. 管理者のコマンド プロンプトを開きます。 管理者のコマンド プロンプトを開くには、以下の手順に従います。
   * **[スタート]** メニューをクリックします。
   * 「**cmd**」と入力します。
   * **[Command Prompt]** を右クリックし、**[管理者として実行]** をクリックします。
3. `InstallCleanup.exe` ユーティリティの完全なパスを入力して、必要なコマンドライン スイッチを渡します。 既定では、ユーティリティのパスは次のようになります。
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

通常は `%ProgramFiles(x86)%\Microsoft Visual Studio` にある `InstallCleanup.exe` が Visual Studio インストーラー ディレクトリの下に見つからない場合は、[Visual Studio のインストール](install-visual-studio.md)の手順に従い、ワークロード選択画面が表示されたら、ウィンドウを閉じて前の手順をもう一度実行します。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 の変更](modify-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
