---
title: Visual Studio インスタンスの検出および管理用のツール
description: クライアント コンピューター上の Visual Studio のインストールを検出して管理するために使用できるツールについて説明します。
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7052908751058b08be8afc3f1c40123ca8ddba48
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280576"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio インスタンスの検出および管理用のツール

クライアント コンピューターでの Visual Studio のインストールの検出と管理に使用できるツールは複数あります。

## <a name="detecting-existing-visual-studio-instances"></a>既存の Visual Studio インスタンスの検出

クライアント コンピューターにインストールされている Visual Studio インスタンスを検出して管理するために役立つ複数のツールが用意されています。

* [VSWhere](https://github.com/microsoft/vswhere): Visual Studio に組み込まれているか、個別のディストリビューションで使用可能な実行可能ファイルです。特定のコンピューター上のすべての Visual Studio インスタンスの場所を見つけるのに役立ちます。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): セットアップ構成 API を使用して Visual Studio のインストール済みインスタンスを識別する PowerShell スクリプトです。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): セットアップ構成 API を使用して既存のインストールを照会する方法を示す C# と C++ のサンプルです。

さらに、[セットアップ構成 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) は、Visual Studio インスタンスを問い合わせるために独自のユーティリティを構築する開発者向けのインターフェイスを提供します。

## <a name="using-vswhereexe"></a>vswhere.exe の使用

`vswhere.exe` は Visual Studio 2017 バージョン 15.2 以降に自動的に組み込まれます。[リリース ページ](https://github.com/Microsoft/vswhere/releases)からダウンロードすることもできます。 ツールのヘルプ情報を取得する場合は `vswhere -?` を使用します。 たとえば、このコマンドでは古いバージョンの製品やプレリリースを含む、Visual Studio のすべてのリリースが表示され、JSON 形式で結果が出力されます。

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Visual Studio 2017 のインストールの詳細については、[Heath Stewart のブログ記事](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)を参照してください。


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Visual Studio インスタンスのレジストリの編集

Visual Studio 2017 ではレジストリ設定はプライベートな場所に保存されているため、同じバージョンの Visual Studio の複数のインスタンスを side-by-side で同じコンピューターで使用できます。

これらのエントリはグローバル レジストリには保存されないため、レジストリ エディターを使用してレジストリ設定を変更するための特別な指示があります。

1. Visual Studio 2017 で開いているインスタンスがある場合は、閉じてください。
2. `regedit.exe` を起動します。
3. `HKEY_LOCAL_MACHINE` ノードを選択します。
4. レジストリ エディターのメイン メニューから **[ファイル] -> [ハイブの読み込み...]** を選択して、**AppData\Local** フォルダーに保存されているプライベート レジストリ ファイルを選択します。 例:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

  > [!NOTE]
  > `<config>` は参照する Visual Studio のインスタンスに対応します。

分離されたハイブの名前になるハイブ名を指定するように求められます。 これを行うと、作成した分離されたハイブの下にあるレジストリを参照できるようになります。

> [!IMPORTANT]
> Visual Studio を再度開始する前に、作成した分離されたハイブをアップロードする必要があります。 これを行うには、レジストリ エディターのメイン メニューから [ファイル] -> [ハイブのアンロード] を選択します。 (これを行わない場合、ファイルがロックされたままになり、Visual Studio で開始することができません。)

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://visualstudio.microsoft.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
