---
title: "Visual Studio for Mac Tools for Unity をセットアップする"
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.topic: article
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: c2290b1165b8d2688b280684e1251b929d002594
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Visual Studio for Mac Tools for Unity をセットアップする

このセクションでは、Visual Studio for Mac Tools for Unity を使い始める方法について説明します。

## <a name="install-visual-studio-for-mac"></a>Visual Studio for Mac をインストールする

Visual Studio for Mac をダウンロードしてインストールします。 無料の Community Edition を含む Visual Studio for Mac のすべてのエディションで、Visual Studio for Mac Tools for Unity がサポートされています。

* Visual Studio for Mac を [visualstudio.com](https://www.visualstudio.com/) からダウンロードします。
* Visual Studio for Mac Tools for Unity は、インストール プロセスの間に自動的にインストールされます。
* インストールに関するその他のヘルプについては、[インストール ガイド](/visualstudio/mac/installation)の手順に従ってください。

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Visual Studio for Mac Tools for Unity 拡張機能が有効になっていることを確認する

Visual Studio for Mac Tools for Unity 拡張機能は既定で有効になりますが、それを確認し、インストールされているバージョン番号を調べることができます。

1.  Visual Studio のメニューから **[拡張機能]** を選びます。

  ![[拡張機能] を選ぶ](media/setup-vsmac-tools-unity-image1.png)

2.  [ゲーム開発] セクションを展開し、Visual Studio for Mac Tools for Unity エントリを確認します。

  ![Unity エントリの表示](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>Unity をインストールする

Visual Studio for Mac Tools for Unity では、Unity バージョン 5.6.1 以降が必要です。 無料の Personal プランを含むすべての Unity プランが、Visual Studio Tools for Unity で動作します。 [store.unity.com](https://store.unity.com/) から Unity をダウンロードします。

> [!NOTE]
> お使いの Unity のバージョンで Visual Studio Tools for Unity が有効になっていることを確認するには、Unity のメニューから **[About Unity]\(Unity について\)** を選び、ダイアログの左下に [Microsoft Visual Studio Tools for Unity enabled]\(Microsoft Visual Studio Tools for Unity は有効です\) と表示されていることを確認します。
>
>   ![Unity について](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Visual Studio for Mac で使用するために Unity を構成する

Unity で Visual Studio を外部スクリプト エディターとして設定する必要があります。

1.  Unity メニューから **[Preferences]\(ユーザー設定\)** を選びます。

  ![[Preferences]\(ユーザー設定\) を選ぶ](media/setup-vsmac-tools-unity-image4.png)

2.  [Preferences]\(ユーザー設定\) ダイアログで、**[External Tools]\(外部ツール\)** タブを選びます。

3.  [External Script Editor]\(外部スクリプト エディター\) ドロップダウン リストから、**[Visual Studio]** が一覧にある場合はそれを選び、ない場合は **[Browse]\(参照\)** を選びます。

  ![Visual Studio を選ぶ](media/setup-vsmac-tools-unity-image5.png)

4.  **[Browse]\(参照\)** を選んだ場合は、[Applications]\(アプリケーション\) ディレクトリに移動し、Visual Studio を選んで、**[Open]\(開く\)** をクリックします。

  ![[Open]\(開く\) を選ぶ](media/setup-vsmac-tools-unity-image6.png)

5.  **[External Script Editor]\(外部スクリプト エディター\)** ボックスの一覧で Visual Studio を選んだ後、[Preferences]\(ユーザー設定\) ダイアログを閉じて構成プロセスを完了します。

