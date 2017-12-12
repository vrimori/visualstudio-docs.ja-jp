---
title: "ファイアウォールまたはプロキシ サーバーの内側に Visual Studio をインストールする | Microsoft Docs"
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 4b203bbc3512ebc59a73a4e1420388a28fdf166b
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>ファイアウォールまたはプロキシ サーバーの内側に Visual Studio をインストールする

Visual Studio インストーラーは、さまざまなドメインと、それらのダウンロード サーバーからファイルをダウンロードします。 このページでは、配置スクリプトに信頼済みとして "ホワイト リスト" に追加することをお勧めするドメイン URL を一覧表示します。

環境に適用可能な場合は、HTTP と HTTPS の両方のプロトコルを使用して次のドメインを追加することを検討してください。

## <a name="microsoft-domains"></a>Microsoft ドメイン
| ドメイン | 目的 |
| ------ | ------- |
| go.microsoft.com | URL の解像度を設定する |
| aka.ms | URL の解像度を設定する |
| download.visualstudio.microsoft.com | パッケージのダウンロード場所を設定する |
| download.microsoft.com | パッケージのダウンロード場所を設定する |
| download.visualstudio.com | パッケージのダウンロード場所を設定する |
| dl.xamarin.com | パッケージのダウンロード場所を設定する |
| visualstudiogallery.msdn.microsoft.com | Visual Studio 拡張機能のダウンロード場所 |
| www.visualstudio.com | ドキュメントの場所 |
| docs.microsoft.com | ドキュメントの場所 |
| msdn.microsoft.com | ドキュメントの場所 |
| www.microsoft.com | ドキュメントの場所 |
| *.windows.net | サインインの場所 |
| *.microsoftonline.com | サインインの場所 |
| *.live.com | サインインの場所 |


## <a name="non-microsoft-domains"></a>Microsoft 以外のドメイン
| ドメイン | 以下のワークロードをインストールします。 |
| ------ | ------- |
| archive.apache.org |  JavaScript でのモバイル開発 <br />(Cordova) |
| cocos2d-x.org | C++ によるゲーム開発 <br />(Cocos) |
| download.epicgames.com | C++ によるゲーム開発 <br />(Unreal Engine) |
| download.oracle.com | JavaScript でのモバイル開発 <br />(Java SDK) <br /><br />.NET によるモバイル開発 <br />(Java SDK) |
| download.unity3d.com | Unity でのゲーム開発 <br />(Unity) |
| netstorage.unity3d.com | Unity でのゲーム開発 <br /> (Unity) |
| dl.google.com | JavaScript でのモバイル開発 <br />(Android SDK および NDK、エミュレーター) <br /><br />.NET によるモバイル開発 <br />(Android SDK および NDK、エミュレーター) |
| www.incredibuild.com | C++ によるゲーム開発 <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | C++ によるゲーム開発 <br />(IncrediBuild) |
| www.python.org | Python 開発 <br />(Python) <br /><br />データ サイエンスと分析のアプリケーション <br />(Python) |

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング](troubleshooting-installation-issues.md)」ページにあるトラブルシューティングのヒントをご覧ください。 また、Visual Studio IDE の [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから製品の問題を Microsoft に報告していただくことや、[UserVoice](https://visualstudio.uservoice.com/forums/121579) でご提案を共有していただくこともできます。 [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。 [Gitter コミュニティの Visual Studio に関する意見交換](https://gitter.im/Microsoft/VisualStudio) ([GitHub](https://github.com/) アカウントが必要) から、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。

## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
  * [ワークロードとコンポーネント ID のリファレンス](workload-and-component-ids.md)
* [Visual Studio 2017 のネットワーク ベース インストールを作成する](create-a-network-installation-of-visual-studio.md)
  * [Visual Studio オフライン インストールに必要な証明書をインストールする](install-certificates-for-visual-studio-offline.md)
* [応答ファイルで Visual Studio インストールを自動化する](automated-installation-with-response-file.md)
* [Visual Studio の展開時にプロダクト キーを自動的に適用する](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Visual Studio 2017 のエンタープライズ展開に既定値を設定する](set-defaults-for-enterprise-deployments.md)
* [パッケージ キャッシュの無効化または移動](disable-or-move-the-package-cache.md)
* [Visual Studio のネットワーク ベース インストールを更新する](update-a-network-installation-of-visual-studio.md)
* [Visual Studio 2017 配置の更新プログラムを制御する](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio インスタンスの検出および管理用のツール](tools-for-managing-visual-studio-instances.md)
