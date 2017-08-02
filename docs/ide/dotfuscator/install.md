---
title: "Dotfuscator Community Edition (CE) をインストールする | Microsoft Docs"
ms.date: 2017-06-22
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, community edition, 難読化, .NET, 無料, Visual Studio 2017, インストール"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
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
description: "Visual Studio 2017 に含まれる無料の Dotfuscator Community Edition をインストールする方法について説明します。"
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: fb5356632ecf8183945b1d50ba940ed05abcf96f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

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

1. **クイック起動** (Ctrl キーを押しながら Q キーを押す) 検索バーで、「`dotfuscator`」と入力します。 <br/> <br/> ![](~/ide/dotfuscator/media/install_from_vs_12.png) <br/> <br/>
2. 表示されたクイック起動の結果の *[インストール]* 見出しで、**[PreEmptive Protection - Dotfuscator (個々のコンポーネント)]** を選択します。
  * または、*[メニュー]* 見出しで、**[ツール] > [PreEmptive Protection - Dotfuscator]** を選択します。この場合、Dotfuscator CE は既にインストールされています。 使用の詳細については、[Dotfuscator CE の完全なユーザー ガイドの概要ページ][get-started]を参照してください。
3. Visual Studio のインストーラー ウィンドウが起動します。このウィンドウは Dotfuscator CE のインストール用に事前に構成されています。
  * 続行するには管理者の資格情報を提供する必要がある場合があります。
4. Visual Studio IDE のすべてのインスタンスを閉じます。 <br/> <br/> ![](~/ide/dotfuscator/media/install_from_vs_345.png) <br/> <br/>
5. Visual Studio インストーラー ウィンドウで、*[インストール]* をクリックします。

インストールが完了したら、Dotfuscator CE の使用を開始できます。 詳細については、[Dotfuscator CE の完全なユーザー ガイドの概要ページ][get-started]を参照してください。

## <a name="during-visual-studio-installation"></a>Visual Studio のインストール中

Visual Studio 2017 をまだインストールしていない場合は、[Visual Studio の Web サイト][2017-install]からインストーラーを取得できます。
実行すると、選択した Visual Studio エディションのインストール オプションが表示されます。

![](~/ide/dotfuscator/media/install_ui.png)

その後、次のように、Visual Studio 2017 の個々のコンポーネントとして Dotfuscator CE をインストールできます。

1. **[個々のコンポーネント]** タブを選択します。
2. *[コード ツール]* で、*[PreEmptive Protection - Dotfuscator]* 項目のチェック ボックスをオンにします。<br/> <br/> ![](~/ide/dotfuscator/media/install_individually_12.png) <br/> <br/>
3. *[概要]* パネルの *[個々のコンポーネント]* セクションに *[PreEmptive Protection - Dotfuscator]* が表示されます。 <br/> <br/> ![](~/ide/dotfuscator/media/install_individually_3.png) <br/> <br/>
4. 使用環境に合わせて、インストール設定をさらに構成します。
5. Visual Studio をインストールする準備ができたら、*[インストール]* ボタンをクリックします。

インストールが完了したら、Dotfuscator CE の使用を開始できます。 詳細については、[Dotfuscator CE の完全なユーザー ガイドの概要ページ][get-started]を参照してください。

## <a name="see-also"></a>関連項目

[Dotfuscator CE の完全なユーザー ガイドのこのトピック][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]: https://www.visualstudio.com/downloads/#vs-2017
[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]: https://www.preemptive.com/products/dotfuscator/downloads

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html

