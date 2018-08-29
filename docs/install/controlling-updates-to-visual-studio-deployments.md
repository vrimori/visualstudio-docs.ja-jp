---
title: Visual Studio 配置の更新プログラムを制御する
description: ネットワークからインストールするときに、Visual Studio が更新プログラムを検索する場所を変更する方法を説明します。
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4f3843b7f3f8f19f0f375d6880d5d8be10bbd2
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "43139315"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>ネットワーク ベースの Visual Studio 配置の更新プログラムを制御する

企業の管理者は、多くの場合、レイアウトを作成してそれをネットワーク ファイル共有でホストし、エンド ユーザーに展開します。

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio が更新プログラムを探す場所を変更する

既定では、インストールがネットワーク共有から展開された場合でも、Visual Studio は引き続きオンラインで更新プログラムを探します。 更新プログラムがある場合、ユーザーがインストールできます。 更新された内容のうちオフライン レイアウトで見つからないものは、すべて Web からダウンロードされます。

Visual Studio が更新プログラムを検索する場所を変更することで直接制御することができます。 ユーザーが更新するバージョンも制御できます。 これを行うには、次の手順を実行します。

 1. オフライン レイアウトを作成します。
    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. それをホストするファイル共有にコピーします。
    ```cmd
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. レイアウトの response.json ファイルを変更し、管理者が制御する channelManifest.json のコピーを指すように `channelUri` 値を変更します。

  値のバックスラッシュは、次の例のように必ずエスケープしてください。

  ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
  ```

 これでエンド ユーザーはこの共有からセットアップを実行し、Visual Studio をインストールできます。
    ```cmd
    \\server\share\VS2017\vs_enterprise.exe
    ```

企業の管理者はユーザーが新しいバージョンの Visual Studio に更新する時期が来たと判断したとき、[レイアウトの場所を更新し](update-a-network-installation-of-visual-studio.md)、次のようにして更新されたファイルを組み込むことができます。

 1. 次のようなコマンドを使用します。
    ```cmd
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 2. 更新後のレイアウトの response.json ファイルにカスタマイズ内容が引き続き含まれているようにします。特に次のような channelUri の変更内容です。
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 このレイアウトからの既存の Visual Studio インストールは `\\server\share\VS2017\ChannelManifest.json` で更新プログラムを探します。 この channelManifest.json がユーザーがインストールしているものより新しい場合、Visual Studio は更新プログラムが利用できることをユーザーに通知します。

 新しいインストールでは、更新されたバージョンの Visual Studio がレイアウトから直接インストールされます。

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE の通知を制御する

上述のとおり、Visual Studio はそのインストール元である場所 (ネットワーク共有やインターネットなど) で更新プログラムが利用できないか確認します。 更新プログラムが利用可能になると、Visual Studio は、ユーザーへの通知としてウィンドウの右上隅に通知フラグを表示します。

 ![更新プログラムの通知フラグ](media/notification-flag.png)

エンドユーザーに更新プログラムを通知したくない場合は、通知を無効にすることができます。 (たとえば、中央のソフトウェア配布メカニズムを使用して更新プログラムを提供する場合、通知を無効にしたい場合があります。)

Visual Studio 2017 は[プライベート レジストリにレジストリ エントリを保存する](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)ので、そのレジストリを通常の方法で直接編集することはできません。 ただし、Visual Studio には `vsregedit.exe` ユーティリティが含まれます。これを利用し、Visual Studio 設定を変更できます。 次のコマンドで通知をオフにできます。

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

(編集したいインストール済みのインスタンスと一致するようにディレクトリを置き換えてください。)

> [!TIP]
> [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) を利用し、クライアント ワークステーションで特定のインスタンスの Visual Studio を見つけます。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio インスタンスの管理用のツール](tools-for-managing-visual-studio-instances.md)
