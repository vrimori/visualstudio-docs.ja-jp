---
title: "Azure 仮想マシンでの Visual Studio の使用 | Microsoft Docs"
description: "Azure 仮想マシンで Visual Studio を使用する方法を説明します"
ms.date: 01/30/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Azure 上の Visual Studio イメージ
構成済みの Azure 仮想マシン (VM) で実行されている Visual Studio を使うのは、何もない状態から開発環境を稼働状態にする最も簡単で速い方法です。  Visual Studio の構成が異なるさまざまなシステム イメージを、[Azure Marketplace](https://portal.azure.com/) で入手できます。 VM を起動して始めるだけです。

まだ Azure を使ったことがない場合は、 [無料の Azure アカウントを作成してください](https://azure.microsoft.com/free)。

## <a name="what-configurations-and-versions-are-available"></a>利用できる構成とバージョン
Azure Marketplace には、最新のメジャー バージョンである Visual Studio 2017 および Visual Studio 2015 のイメージがあります。  メジャー バージョンごとに、最初にリリースされた ( "RTW" とも呼ばれます) バージョンと、"最新" の更新バージョンがあります。  これらの異なるバージョンごとに、Visual Studio Enterprise エディションと Visual Studio Community エディションがあります。  これらのイメージは少なくとも毎月更新され、Visual Studio と Windows の最新の更新プログラムが組み込まれます。  イメージの名前は同じままですが、各イメージの説明にはインストールされる製品バージョンとイメージの "有効" 期日が含まれます。

|               リリース バージョン              |        エディション       |     製品バージョン     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017 - 最新 (バージョン 15.5) | Enterprise、Community |      バージョン 15.5.3     |
|         Visual Studio 2017 - RTW           | Enterprise、Community |      バージョン 15.0.7     |
|   Visual Studio 2015 - 最新 (Update 3)   | Enterprise、Community |  バージョン 14.0.25431.01  |
|         Visual Studio 2015 - RTW           |         なし          | (サービス有効期限切れ) |

> [!NOTE]
> Microsoft のサービス ポリシーに従うと、Visual Studio 2015 の最初にリリースされた ("RTW" とも呼ばれます) バージョンは、サービスの有効期限が切れています。  したがって、Visual Studio 2015 製品ラインに提供されるバージョンとして残っているのは Visual Studio 2015 Update 3 だけです。

詳細については、[Visual Studio サービス ポリシー](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs)に関する説明を参照してください。

## <a name="what-features-are-installed"></a>インストールされる機能
各イメージには、その Visual Studio エディションの推奨される機能が含まれます。  一般に、インストールには次のものが含まれます。

* 利用可能なすべてのワークロードと、そのワークロードの推奨されるオプション コンポーネント
* .NET 4.6.2 と .NET 4.7 SDK、Targeting Pack、開発者ツール
* Visual F#
* Visual Studio 向け GitHub 拡張
* LINQ to SQL ツール

次に示すのは、イメージをビルドするときに Visual Studio のインストールに使われるコマンド ラインです。

```
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^ 
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

イメージに必要な Visual Studio の機能が含まれない場合は、フィードバック ツール (ページの右上隅) を使ってそのことをフィードバックしてください。

## <a name="what-size-vm-should-i-choose"></a>VM のサイズの選択
新しい仮想マシンは簡単にプロビジョニングでき、Azure では全範囲の仮想マシン サイズが提供されています。  ハードウェアを調達するときはいつでも同じですが、パフォーマンスとコストのバランスを考える必要があります。  Visual Studio は高性能のマルチスレッド アプリケーションなので、少なくとも 2 つのプロセッサと 7 GB のメモリを含む VM サイズが必要です。 Azure では、これは少なくとも以下の VM サイズに対応します。

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

最新のマシンのサイズについては、「[Azure の Windows 仮想マシンのサイズ](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes)」を参照してください。

Azure では、最初の選択に縛られることはありません。VM のサイズを変更することで、最初の選択を再調整できます。  より適切なサイズで新しい VM をプロビジョニングしたり、既存の VM のサイズを異なる基盤ハードウェアに合わせて変更したりできます。  詳細については、「[Windows VM のサイズ変更](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm)」を参照してください。

## <a name="after-i-get-the-vm-running-then-what"></a>VM を実行してからの作業
Visual Studio は、Azure の "ライセンス持ち込み" モデルに従います。  そのため、専用ハードウェアへのインストールと同様に、最初に行うことの 1 つは、Visual Studio のインストールのライセンスを有効にすることです。  Visual Studio のサブスクリプションに関連付けられている Microsoft アカウントを使ってサインインすることで、または初期購入時のプロダクト キーを使うことで、Visual Studio のロックを解除できます。  詳細については、「[Visual Studio にサインイン](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio)」および「[Visual Studio のロックを解除する方法](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio)」を参照してください。

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>開発用 VM を構築した後、将来またはチームの使用のために VM を保存 (キャプチャ) する方法

開発環境の範囲は広大であり、環境が複雑になるほどその構築にはコストがかかります。  ただし、環境の構成に関係なく、Azure では、自分自身やチームの他のメンバーが将来使えるように、完全に構成された VM を "基本イメージ" として保存/キャプチャすることで、投資を簡単に保護できます。  その後は、新しい VM を起動するときに、Marketplace イメージではなく基本イメージからプロビジョニングします。

簡単にまとめると、sysprep を実行してから実行中の VM をシャットダウンし、Azure Portal の UI を使ってイメージとして VM を "*キャプチャ (図 1)*" する必要があります。  Azure は、イメージを含む `.vhd` ファイルをユーザーが選んだストレージ アカウントに保存します。  その後、新しいイメージはサブスクリプションのリソース一覧にイメージ リソースとして表示されます。

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(図 1) Azure Portal の UI を使ってイメージをキャプチャする。*</center>

詳細については、[イメージへの VM のキャプチャ](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource)に関する説明を参照してください。

  **注意:** 忘れずに VM の sysprep を行ってください。  そうしないと、Azure はイメージから VM をプロビジョニングできません。

> [!NOTE]
> イメージの保存にはやはり若干のコストがかかりますが、その増加分は、VM を必要とするチーム内のユーザーごとに、一から VM を再構築するための人件費に比べればたいしたことはないはずです。  たとえば、チームのすべてのメンバーが再利用可能な 127 GB のイメージを作成して 1 か月保存するには数ドルのコストがかかります。  ただし、そのコストは、各従業員が使うために適切に構成された開発用コンピューターを構築するための従業員の作業時間数と比べればわずかなものです。

さらに、さまざまな開発構成や複数のコンピューター構成のように、開発タスクやテクノロジをさらに広げることが必要な場合があります。  Azure DevTest Labs を使うと、"ゴールデン イメージ" の構築を自動化する "_レシピ_" を作成し、チームで実行する VM のポリシーを管理することができます。  「[開発者のための Azure DevTest Labs の使用](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab)」は、DevTest Labs の詳細についての最適なソースです。

## <a name="next-steps"></a>次の手順
事前構成済みの Visual Studio イメージについて理解したので、次のステップは新しい VM の作成です。

* [Azure Portal で VM を作成する](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Windows の仮想マシンの概要](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)
