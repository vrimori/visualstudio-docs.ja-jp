---
title: "ファイアウォールまたはプロキシ サーバーの内側に Visual Studio をインストールする | Microsoft Docs"
description: 
ms.custom: 
ms.date: 07/18/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
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
ms.translationtype: HT
ms.sourcegitcommit: ddbbda1069749e2ce685507d55a070f1dec27c17
ms.openlocfilehash: 48fd143f917d6e13c18f6913bea625b2e8cf5ce8
ms.contentlocale: ja-jp
ms.lasthandoff: 07/19/2017

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
| msdn.microsoft.com | ドキュメントの場所 |
| www.microsoft.com | ドキュメントの場所 |

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

## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
  * [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
    * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
    * [ワークロードとコンポーネント ID のリファレンス](workload-and-component-ids.md)
  * [Visual Studio のネットワーク ベース インストールを作成する](create-a-network-installation-of-visual-studio.md)
    * [オフライン環境での Visual Studio のインストールに関する特別な考慮事項](install-visual-studio-in-offline-environment.md)
  * [応答ファイルで Visual Studio を自動化する](automated-installation-with-response-file.md)
  * [Visual Studio の展開時にプロダクト キーを自動的に適用する](automatically-apply-product-keys-when-deploying-visual-studio.md)
  * [Visual Studio のエンタープライズ展開に既定値を設定する](set-defaults-for-enterprise-deployments.md)
  * [パッケージ キャッシュの無効化または移動](disable-or-move-the-package-cache.md)
  * [Visual Studio のネットワーク ベース インストールを更新する](update-a-network-installation-of-visual-studio.md)
  * [Visual Studio 配置の更新プログラムを制御する](controlling-updates-to-visual-studio-deployments.md)
  * [Visual Studio インスタンスの検出および管理用のツール](tools-for-managing-visual-studio-instances.md)
  * [Visual Studio 2017 で問題を報告する](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

