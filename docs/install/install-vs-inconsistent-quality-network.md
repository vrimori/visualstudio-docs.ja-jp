---
title: 低帯域幅または信頼性の低いネットワーク環境にインストールする | Microsoft Docs
description: ネットワークが信頼できないか低帯域幅のときに Visual Studio インストーラーを使用する方法、およびコマンド ラインを使用してインストール ファイルをダウンロードする方法を説明します。
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: b273efb06e7b2e70617d28dcafc85735bcfb1fd1
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138801"
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>低帯域幅または信頼性の低いネットワーク環境に Visual Studio 2017 をインストールする

Visual Studio Web インストーラーを試してみてください。ほとんどの場合にその利便性を実感していただけるものと考えております。

 > [!div class="button"]
 > [Visual Studio 2017 をダウンロードする](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

ただし、インターネット接続を利用できない場合、またはその信頼性が低い場合は、コマンド ラインを使って、オフライン インストールを実行するために必要なファイルのローカル キャッシュを作成できます。 ここではその方法を説明します。

> [!NOTE]
> 企業の IT 管理者が、インターネットからファイアウォールで隔てられたクライアント ワークステーションのネットワークに Visual Studio 2017 を展開する場合は、「[Visual Studio 2017 のネットワーク インストールを作成する](../install/create-a-network-installation-of-visual-studio.md)」と「[Visual Studio オフライン インストールに必要な証明書をインストールする](../install/install-certificates-for-visual-studio-offline.md)」をご覧ください。

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>ステップ 1 - Visual Studio ブートストラップをダウンロードする

最初に、選択したエディションの Visual Studio の Visual Studio ブートストラップをダウンロードします。

セットアップ ファイル&mdash; (具体的にはブートストラップ ファイル)&mdash; は、次のいずれかになります (あるいは同様のファイル)。

| エディション                    | ファイル                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio コミュニティ    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>ステップ 2 - ローカル インストール キャッシュを作成する

このステップを実行するにはインターネット接続が必要です。 ローカル レイアウトを作成するには、コマンド プロンプトを開き、次の例にあるいずれかのコマンドを使用します。 この例では、Visual Studio の Community Edition を使用することを前提としています。ご利用のエディションに応じて適切なコマンドに修正してください。

- .NET Web と .NET デスクトップ開発の場合、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- .NET デスクトップと Office 開発の場合、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- C++ デスクトップ開発の場合、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- すべての機能を備えた完全なローカル レイアウトを作成するには (_多くの_機能があるため、これには時間がかかります)、次を実行します。

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

英語以外の言語をインストールする場合、このページの下の一覧にあるロケールに `en-US` を変更します。 この[利用できるコンポーネントとワークロードの一覧](workload-and-component-ids.md)を利用し、必要に応じて、インストール キャッシュをさらにカスタマイズできます。

> [!IMPORTANT]
> Visual Studio 2017 の完全なレイアウトでは、少なくとも 35 GB のディスク領域が必要で、ある程度ダウンロードに時間がかかります。 インストールするコンポーネントのみでレイアウトを作成する方法については、「[コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)」をご覧ください。

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>ステップ 3 - ローカル キャッシュから Visual Studio をインストールする

> [!TIP]
> ローカル インストール キャッシュから実行するとき、セットアップは各ファイルのローカル バージョンを使います。 ただし、インストール中にキャッシュにないコンポーネントを選択すると、インターネットからのダウンロードが試みられます。

ダウンロードしたファイルのみがインストールされるように、レイアウト キャッシュの作成に利用したものと同じコマンド ライン オプションを使用します。 たとえば、次のコマンドでレイアウト キャッシュを作成した場合、

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

インストールを実行するには次のコマンドを使用します。

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> 署名が無効であるというエラーが発生する場合は、更新された証明書をインストールする必要があります。 オフライン キャッシュ内の証明書フォルダーを開きます。 各証明書ファイルをダブルクリックした後、証明書マネージャー ウィザードの指示に従って操作します。 パスワードを求められたら、空のままにしてください。

## <a name="list-of-language-locales"></a>言語ロケールの一覧

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

* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 のワークロード ID とコンポーネント ID](workload-and-component-ids.md)
