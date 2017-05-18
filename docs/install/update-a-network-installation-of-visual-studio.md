---
title: "Visual Studio のネットワーク ベース インストールを更新する | Microsoft Docs"
description: "{{プレースホルダー}}"
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Visual Studio のネットワーク ベース インストールを更新する

ネットワーク インストール レイアウトを Visual Studio の最新のインストール ポイントとして使用できるように、また、クライアント ワークステーションに既に配置されているインストールを保持するために、最新の製品の更新プログラムを使って Visual Studio のネットワーク インストール レイアウトを更新できます。

## <a name="how-to-update-a-network-layout"></a>ネットワーク レイアウトの更新方法
最新の更新プログラムが含まれるように、ネットワーク インストールの共有を更新するには、レイアウトを最初に作成するときに実行したものと同じ `--layout` コマンドを実行して、更新されたパッケージの増分をダウンロードします。

最初にネットワーク レイアウトを作成するときに部分的なレイアウトを選択した場合は、最初にネットワーク インストール レイアウトを作成したときに使用したものと同じコマンドライン パラネーターを使用してください (つまり、同じワークロードおよび言語)。 複数のオプションを選んだ場合、2 つ目の `--layout` コマンドが、2 回目を指定していなかったパッケージを更新することはありません。

ファイル共有上にレイアウトをホストしている場合は、レイアウトのプライベート コピーを更新し (例: `c:\vs2017offline`)、すべての更新されたコンテンツがダウンロードされた後に、ファイル共有にコピーします (例: `\\server\products\VS2017`)。  この操作を行わない場合は、レイアウトの更新中にユーザーがセットアップを実行しても、レイアウトは完全に更新されていないため、レイアウトからすべてのコンテンツを取得することはできない可能性が高くなります。

## <a name="how-to-deploy-an-update-to-client-machines"></a>クライアント マシンに更新を配置する方法
ネットワーク環境が構成される方法によって、更新プログラムをエンタープライズ管理者が配置することも、クライアント マシンから開始することもできます。 

- ユーザーは、オフラインのインストール フォルダーからインストールした Visual Studio インスタンスを更新することができます。
  - Visual Studio インストーラーを実行します。
  - 次に、**[更新]** をクリックします。

- 管理者は、次の 2 つの別々のコマンドを使用して、ユーザーの相互作用なしに、Visual Studio のクライアント展開を更新できます。
  - 最初に、Visual Studio インストーラーを更新します。 <br>```vs_enterprise.exe --quiet --update```
  - 次に、Visual Studio アプリケーション自体を更新します。 <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> [vswhere.exe コマンド](tools-for-managing-visual-studio-instances.md)を使用して、クライアント コンピューター上にある Visual Studio の既存のインスタンスのインストール パスを特定します。

> [!TIP]
> 更新通知をユーザーに表示するときの制御方法の詳細については、「[Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md)」 (ネットワーク ベースの Visual Studio 配置の更新プログラムを制御する) を参照してください。


## <a name="see-also"></a>関連項目
* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio インスタンスの検出および管理用のツール](tools-for-managing-visual-studio-instances.md)
* [ネットワーク ベースの Visual Studio 配置の更新プログラムを制御する](controlling-updates-to-visual-studio-deployments.md)

