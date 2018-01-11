---
title: "低帯域幅または信頼性の低いネットワーク環境にインストールする | Microsoft Docs"
description: "信頼性の低いネットワーク環境における Visual Studio インストーラーの動作とインストールの開始前にインストール ファイルをダウンロードする方法について説明します。"
ms.date: 08/30/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1d7b9b7084b91ace1f76d4d411f117df41cfd257
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>低帯域幅または信頼性の低いネットワーク環境に Visual Studio 2017 をインストールする

Visual Studio Web インストーラーを試してみてください。ほとんどの場合にその利便性を実感していただけるものと考えております。

 > [!div class="button"]
 > [Visual Studio 2017 をダウンロードする](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

ただし、インターネット接続を利用できない場合、またはその信頼性が低い場合は、コマンド ラインを使って、オフライン インストールを実行するために必要なファイルのローカル キャッシュを作成できます。 ここではその方法を説明します。

> [!NOTE]
> 企業の IT 管理者が、インターネットからファイアウォールで隔てられたクライアント ワークステーションのネットワークに Visual Studio 2017 を展開する場合は、「[Visual Studio 2017 のネットワーク インストールを作成する](../install/create-a-network-installation-of-visual-studio.md)」と「[オフライン環境での Visual Studio のインストールに関する特別な考慮事項](../install/install-visual-studio-in-offline-environment.md)」をご覧ください。

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>ステップ 1 - Visual Studio ブートストラップをダウンロードする

最初に、選択したエディションの Visual Studio の Visual Studio ブートストラップをダウンロードします。

セットアップ ファイル&mdash; (具体的にはブートストラップ ファイル)&mdash; は、次のいずれかになります (あるいは同様のファイル)。

| エディション                    | ファイル                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio コミュニティ    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>ステップ 2 - ローカル インストール キャッシュを作成する

このステップを実行するにはインターネット接続が必要です。 ローカル レイアウトを作成するには、コマンド プロンプトを開き、次の例にあるいずれかのコマンドを使います。この例では、Visual Studio の Community Edition を使っていることを前提としています。お使いのエディションに応じてコマンドを適切に調整してください。

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

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目
* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
