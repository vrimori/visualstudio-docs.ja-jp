---
title: "Visual Studio 配置の更新プログラムを制御する | Microsoft Docs"
description: "{{プレースホルダー}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>ネットワーク ベースの Visual Studio 配置の更新プログラムを制御する

企業の管理者は、多くの場合、レイアウトを作成してそれをネットワーク ファイル共有でホストし、エンド ユーザーに展開します。

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio が更新プログラムを探す場所を変更する
既定では、インストールがネットワーク共有から展開された場合でも、Visual Studio は引き続きオンラインで更新プログラムを探します。 更新プログラムが利用できる場合、ユーザーはそれをインストールできます。オフライン レイアウトにない更新済みコンテンツは Web からダウンロードされます。

Visual Studio が更新プログラムを探す場所と更新後のバージョンを直接制御する場合、次の手順で Visual Studio が更新プログラムを探す場所を変更できます。

 1. オフライン レイアウトを作成します。
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. それをホストするファイル共有にコピーします。
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. レイアウトの response.json ファイルを変更し、管理者が制御する channelManifest.json のコピーを指すように `channelUri` 値を変更します。 <b>注:</b> 次のように、値のバックスラッシュを必ずエスケープしてください。
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. これでエンド ユーザーはこの共有からセットアップを実行し、Visual Studio をインストールできます。
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. 企業の管理者はユーザーが新しいバージョンの Visual Studio に更新する時期が来たと判断したとき、[レイアウトの場所を更新し](update-a-network-installation-of-visual-studio.md)、更新されたファイルを組み込むことができます。次のようなコマンドを利用します。
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. 更新後のレイアウトの response.json ファイルにカスタマイズ内容が引き続き含まれているようにします。特に channelUri の変更内容です。
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. このレイアウトからの既存の Visual Studio インストールは `\\server\share\VS2017\ChannelManifest.json` で更新プログラムを探します。 この channelManifest.json がユーザーがインストールしているものより新しい場合、Visual Studio は更新プログラムが利用できることをユーザーに通知します。
 8. 新しいインストールでは、更新されたバージョンの Visual Studio がレイアウトから直接インストールされます。

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE の通知を制御する
上述のとおり、Visual Studio はそのインストール元である場所 (ネットワーク共有やインターネットなど) で更新プログラムが利用できないか確認します。 更新プログラムが利用可能になると、Visual Studio の既定では、ユーザーへの通知としてウィンドウの右上隅に通知フラグが表示されます。![更新プログラムの通知フラグ](~/docs/install/media/notification-flag.png)

エンド ユーザーに更新を通知しない場合 (中央のソフトウェア配布機構で更新プログラムを届ける場合など)、通知を無効にできます。

Visual Studio 2017 は[プライベート レジストリにレジストリ エントリを保存する](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)ので、そのレジストリを通常の方法で直接編集することはできません。 ただし、Visual Studio にはコマンド `vsregedit.exe` が含まれます。これを利用し、Visual Studio 設定を変更できます。 次のコマンドで通知をオフにできます。

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

編集するインストール済みインスタンスに合わせ、上記のコマンドのディレクトリを置換します。 

> [!TIP]
> [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) を利用し、クライアント ワークステーションで特定のインスタンスの Visual Studio を見つけます。 

## <a name="see-also"></a>関連項目
* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio インスタンスの管理用のツール](tools-for-managing-visual-studio-instances.md)

