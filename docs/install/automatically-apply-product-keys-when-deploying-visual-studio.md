---
title: Visual Studio の展開時にプロダクト キーを自動的に適用する
description: Visual Studio を展開するときに、プロダクト キーをプログラムで適用する方法を説明します。
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 122fbaa30b90eb7cb5f7cb5de210e86155573833
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio の展開時にプロダクト キーを自動的に適用する

Visual Studio の配置を自動化するために使用されるスクリプトの一部として、プログラム的にプロダクト キーを適用することができます。 プロダクト キーは、Visual Studio のインストール中またはインストール完了後に、プログラム的にデバイスで設定できます。

## <a name="apply-the-license-after-installation"></a>インストール後にライセンスを適用する

 ターゲット コンピューターにある `StorePID.exe` ユーティリティをサイレント モードで使用して、インストールされているバージョンの Visual Studio をプロダクト キーでアクティブにすることができます。 `StorePID.exe` は次の既定の場所に Visual Studio 2017 をインストールするユーティリティ プログラムです。 <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 System Center エージェントまたは管理者特権でのコマンド プロンプトを使用して、昇格された特権で `StorePID.exe` を実行します。 これに続いてプロダクト キーと Microsoft 製品コード (MPC) を入力します。

>[!IMPORTANT]
> プロダクト キーには、ダッシュ (-) を含めてください。

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

 次の例は Visual Studio 2017 Enterprise にライセンスを適用するコマンド ラインです。MPC は 08860 で、プロダクト キーは `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` です。既定の場所にインストールするものと想定しています。

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 次の表に、Visual Studio の各エディションの MPC コードを一覧します。

| Visual Studio エディション                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

`StorePID.exe` が正常にプロダクト キーを適用した場合は `%ERRORLEVEL%` として 0 を返します。 エラーが発生した場合、エラーの状態に基づいて次のいずれかのコードが返されます。

| Error                     | コード |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio のインストール](../install/install-visual-studio.md)
* [Visual Studio のオフライン インストールを作成する](../install/create-an-offline-installation-of-visual-studio.md)
