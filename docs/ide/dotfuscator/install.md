---
title: Dotfuscator Community Edition (CE) をインストールする
ms.date: 06/22/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, 難読化, .NET, 無料, Visual Studio 2017, インストール
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Visual Studio 2017 に含まれる無料の Dotfuscator Community Edition をインストールする方法について説明します。
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: dc0a366eadfb5a077fdc2a7d346ef5f3638afe27
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948525"
---
# <a name="install-dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE) をインストールする

Visual Studio 2017 には、影響の少ない新しいインストール エクスペリエンスが導入されています。
そのため、Dotfuscator Community Edition (Dotfuscator CE) は既定ではインストールされません。
ただし、Visual Studio を既にインストールしている場合でも、Dotfuscator CE は簡単にインストールできます。

> [!NOTE]
> 各リリースの Visual Studio に付属の Dotfuscator CE のバージョンだけでなく、PreEmptive Solutions も Web サイトで定期的に更新バージョンが提供されます。
> Visual Studio からインストールするのではなく、**最新バージョン**を直接ダウンロードする場合は、**[ここをクリックして Dotfuscator のダウンロード ページに移動してください][download]**。

## <a name="within-visual-studio"></a>Visual Studio 内

次のようにして、Visual Studio IDE から Dotfuscator CE をインストールすることができます。

1. **クイック起動** (Ctrl キーを押しながら Q キーを押す) 検索バーで、「`dotfuscator`」と入力します。 <br/> <br/> ![クイック起動](media/install_from_vs_12.png) <br/> <br/>
2. 表示されたクイック起動の結果の *[インストール]* 見出しで、**[PreEmptive Protection - Dotfuscator (個々のコンポーネント)]** を選択します。
   * または、*[メニュー]* 見出しで、**[ツール] > [PreEmptive Protection - Dotfuscator]** を選択します。この場合、Dotfuscator CE は既にインストールされています。 使用の詳細については、[Dotfuscator CE の完全なユーザー ガイドの概要ページ][get-started]を参照してください。
3. Visual Studio のインストーラー ウィンドウが起動します。このウィンドウは Dotfuscator CE のインストール用に事前に構成されています。
   * 続行するには管理者の資格情報を提供する必要がある場合があります。
4. Visual Studio IDE のすべてのインスタンスを閉じます。 <br/> <br/> ![[インストール] をクリックします](media/install_from_vs_345.png) <br/> <br/>
5. Visual Studio インストーラー ウィンドウで、*[インストール]* をクリックします。

インストールが完了したら、Dotfuscator CE の使用を開始できます。 詳細については、[Dotfuscator CE の完全なユーザー ガイドの概要ページ][get-started]を参照してください。

## <a name="during-visual-studio-installation"></a>Visual Studio のインストール中

Visual Studio 2017 をまだインストールしていない場合は、[Visual Studio の Web サイト][2017-install]からインストーラーを取得できます。
実行すると、選択した Visual Studio エディションのインストール オプションが表示されます。

![インストール オプション](media/install_ui.png)

その後、次のように、Visual Studio 2017 の個々のコンポーネントとして Dotfuscator CE をインストールできます。

1. **[個々のコンポーネント]** タブを選択します。
2. *[コード ツール]* で、*[PreEmptive Protection - Dotfuscator]* 項目のチェック ボックスをオンにします。<br/> <br/> ![個々のコンポーネント](media/install_individually_12.png) <br/> <br/>
3. *[概要]* パネルの *[個々のコンポーネント]* セクションに *[PreEmptive Protection - Dotfuscator]* が表示されます。 <br/> <br/> ![概要ペイン](media/install_individually_3.png) <br/> <br/>
4. 使用環境に合わせて、インストール設定をさらに構成します。
5. Visual Studio をインストールする準備ができたら、*[インストール]* ボタンをクリックします。

インストールが完了したら、Dotfuscator CE の使用を開始できます。 詳細については、[Dotfuscator CE の完全なユーザー ガイドの概要ページ][get-started]を参照してください。

## <a name="see-also"></a>関連項目

[This topic in the full Dotfuscator CE User Guide]: https://www.preemptive.com/dotfuscator/ce/docs/help/

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]:  https://visualstudio.microsoft.com/downloads/#vs-2017
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html