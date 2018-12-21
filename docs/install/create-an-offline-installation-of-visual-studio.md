---
title: オフライン インストールを作成する
description: インターネット接続の信頼性が低い場合や帯域幅が低い場合にオフラインで Visual Studio をインストールする方法について説明します。
ms.custom: seodec18
ms.date: 08/28/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37d218893ab16a8d0907e608ebeb3b02ab944385
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159985"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Visual Studio 2017 のオフライン インストールを作成する

Visual Studio 2017 はさまざまなネットワークとコンピューターの構成で問題なく動作するように設計されています。 [Visual Studio Web インストーラー](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;ファイルが小さく、最新の修正プログラムと機能がすべて含まれています&mdash;の利用をお勧めしますが、それが難しい場合もあると思います。

たとえば、インターネット接続の信頼性が低い場合や帯域幅が低い場合があるでしょう。 その場合、いくつかの選択肢があります。新しい "全部ダウンロードしてからインストールする" 機能を使用してインストール前にファイルをダウンロードするか、コマンド ラインを使用してファイルのローカル キャッシュを作成することができます。

> [!NOTE]
> 企業の IT 管理者が、インターネットからファイアウォールで隔てられたクライアント ワークステーションのネットワークに Visual Studio 2017 を展開する場合は、「[Visual Studio 2017 のネットワーク インストールを作成する](../install/create-a-network-installation-of-visual-studio.md)」と「[Visual Studio オフライン インストールに必要な証明書をインストールする](../install/install-certificates-for-visual-studio-offline.md)」をご覧ください。

## <a name="use-the-download-all-then-install-feature"></a>"全部ダウンロードしてからインストールする" 機能を使用する

[**15.8 の新機能**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017#install
):Web インストーラーをダウンロードした後、Visual Studio インストーラーから **[Download all, then install]\(全部ダウンロードしてからインストールする\)** オプションを選択します。 次に、インストールを続行します。

   !["全部ダウンロードしてからインストールする" オプション](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>コマンドラインを使用してローカル キャッシュを作成する

小規模のブートストラップをダウンロードした後、コマンド ラインを使用してローカル キャッシュを作成します。 次に、ローカル キャッシュを使用して Visual Studio をインストールします。 (このプロセスは以前のバージョンで利用できた ISO ファイルに置き換わるものです。)

ここではその方法を説明します。

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>ステップ 1 - Visual Studio ブートストラップをダウンロードする

このステップを実行するにはインターネット接続が必要です。

最初に、選択したエディションの Visual Studio の Visual Studio ブートストラップをダウンロードします。 セットアップ ファイル&mdash;またはブートストラップ&mdash;は、次のいずれかになります (あるいは同様のファイル)。

| エディション                    | ファイル                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio コミュニティ    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

### <a name="step-2---create-a-local-install-cache"></a>ステップ 2 - ローカル インストール キャッシュを作成する

このステップを実行するにはインターネット接続が必要です。

> [!IMPORTANT]
> Visual Studio Community 2017 をインストールする場合、インストールしてから 30 日以内にアクティブ化する必要があります。 これにはインターネット接続が必要です。

コマンド プロンプトを開き、次の例にあるいずれかのコマンドを使用します。 ここに挙げた例は、Visual Studio の Community Edition を使用することを前提としています。ご利用のエディションに応じて適切なコマンドに修正してください。

- .NET Web と .NET デスクトップ開発の場合、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- .NET デスクトップと Office 開発の場合、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- C++ デスクトップ開発の場合、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- すべての機能を備えた完全なローカル レイアウトを作成するには (_多くの_機能があるため、これには時間がかかります)、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

英語以外の言語をインストールする場合、`en-US` を[言語ロケールの一覧](#list-of-language-locales)にあるロケールに変更します。 次に、[利用できるコンポーネントとワークロードの一覧](workload-and-component-ids.md)を利用して、インストール キャッシュをさらにカスタマイズします。

> [!IMPORTANT]
> Visual Studio 2017 の完全なレイアウトでは、少なくとも 35 GB のディスク領域が必要で、ある程度ダウンロードに時間がかかります。 インストールするコンポーネントのみでレイアウトを作成する方法については、「[コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)」をご覧ください。

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>ステップ 3 - ローカル キャッシュから Visual Studio をインストールする

> [!TIP]
> ローカル インストール キャッシュから実行するとき、セットアップは各ファイルのローカル バージョンを使います。 ただし、インストール中にキャッシュにないコンポーネントを選択すると、セットアップ中にインターネットからのダウンロードが試みられます。

以前にダウンロードしたファイルのみがインストールされるように、レイアウト キャッシュの作成に利用したものと同じコマンド ライン オプションを使用します。 たとえば、次のコマンドでレイアウト キャッシュを作成した場合、

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

次に、このコマンドを使用してインストールを実行します。

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> 署名が無効であるというエラーが発生する場合は、更新された証明書をインストールする必要があります。 オフライン キャッシュ内の証明書フォルダーを開きます。 各証明書ファイルをダブルクリックした後、証明書マネージャー ウィザードの指示に従って操作します。 パスワードを求められたら、空のままにしてください。

### <a name="list-of-language-locales"></a>言語ロケールの一覧

| **言語ロケール** | **Language** |
| ----------------------- | --------------- |
| cs-CZ | チェコ語 |
| de-DE | ドイツ語 |
| en-US | 英語 |
| es-ES | スペイン語 |
| fr-FR | フランス語 |
| it-IT | イタリア語 |
| ja-JP | 日本語 |
| ko-KR | 韓国語 |
| pl-PL | ポーランド語 |
| pt-BR | ポルトガル語 - ブラジル |
| ru-RU | ロシア語 |
| tr-TR | トルコ語 |
| zh-CN | 中国語 - 簡体字 |
| zh-TW | 中国語 - 繁体字 |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

- [Visual Studio 2017 のネットワーク インストールを作成する](../install/create-a-network-installation-of-visual-studio.md)
- [Visual Studio オフライン インストールに必要な証明書をインストールする](../install/install-certificates-for-visual-studio-offline.md)
- [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 2017 のワークロード ID とコンポーネント ID](workload-and-component-ids.md)
