---
title: Visual Studio 2017 のワークロード ID とコンポーネント ID
description: ワークロード ID とコンポーネント ID を使用して、コマンドラインを使用して Visual Studio をインストールするか、VSIX マニフェストで依存関係として指定します。
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 05/07/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: 34e19ef1-abfb-44fd-aad2-33c5d7874482
ms.workload:
- multiple
ms.openlocfilehash: 1c3f21735a67c205308126bfe50d69ad7e2b22b4
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870989"
---
# <a name="visual-studio-2017-workload-and-component-ids"></a>Visual Studio 2017 のワークロード ID とコンポーネント ID

コマンド ラインを使用して Visual Studio をインストールする場合や、VSIX マニフェストで依存関係として指定する場合に必要となる使用可能なワークロードとコンポーネント ID を表示するには、以下の表のエディション名をクリックします。

| **エディション** | **ID** | **説明** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2017](workload-component-id-vs-enterprise.md) | Microsoft.VisualStudio.Product.Enterprise | 任意の規模のチームにわたって生産性を高め調整を容易にする Microsoft DevOps ソリューションです。 |
| [Visual&nbsp;Studio Professional&nbsp;2017](workload-component-id-vs-professional.md) | Microsoft.VisualStudio.Product.Professional | 小規模なチームを対象としたプロフェッショナル開発者用ツールとサービスです。 |
| [Visual&nbsp;Studio Community&nbsp;2017](workload-component-id-vs-community.md) | Microsoft.VisualStudio.Product.Community | 学生、オープン ソース、個人の開発者向けの無料でフル機能の IDE です。 |
| [Visual&nbsp;Studio Team&nbsp;Explorer&nbsp;2017](workload-component-id-vs-team-explorer.md) | Microsoft.VisualStudio.Product.TeamExplorer | Visual Studio 開発者向けツールなしで Team Foundation Server および Visual Studio Team Services を操作できます。 |
| [Visual Studio Desktop Express 2017](workload-component-id-vs-express.md) | Microsoft.VisualStudio.Workload.WDExpress | 構文認識コード編集、ソース コード管理、作業項目管理を備える WPF、WinForms、Win32 などのネイティブおよびマネージ アプリケーションのビルド。 C#、Visual Basic、Visual C++ のサポートが含まれます。 |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2017](workload-component-id-vs-build-tools.md) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools を使用すると、Visual Studio IDE を必要とせずに、MSBuild ベースのネイティブおよびマネージ アプリケーションをビルドできます。 Visual C++ コンパイラやライブラリ、MFC、ATL、C++/CLI サポートをインストールするオプションもあります。 |
| [Visual&nbsp;Studio Test&nbsp;Agent&nbsp;2017](workload-component-id-vs-test-agent.md)  | Microsoft.VisualStudio.Product.TestAgent | 自動テストとロード テストのリモートでの実行をサポートします。 |
| [Visual&nbsp;Studio Test&nbsp;Controller 2017 ](workload-component-id-vs-test-controller.md) | Microsoft.VisualStudio.Product.TestController | 複数のマシンに自動テストを配布します |
| [Visual&nbsp;Studio Test&nbsp;Professional&nbsp;2017](workload-component-id-vs-test-professional.md) | Microsoft.VisualStudio.Product.TestProfessional | Visual Studio Test Professional 2017 |
| [Visual&nbsp;Studio Feedback&nbsp;Client&nbsp;2017](workload-component-id-vs-feedback-client.md) | Microsoft.VisualStudio.Product.FeedbackClient | Visual Studio Feedback Client 2017 |

これらの一覧を使用する方法について詳しくは、「[コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)」および「[How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」(機能拡張プロジェクトを Visual Studio 2017 に移行する方法) をご覧ください。

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 の管理者ガイド](visual-studio-administrator-guide.md)
* [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio 2017 のインストールに使用するコマンド ライン パラメーターの例](command-line-parameter-examples.md)
