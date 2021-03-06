---
title: Visual Studio 管理者ガイド
titleSuffix: ''
description: エンタープライズ環境で Visual Studio を展開する方法について説明します。
ms.date: 05/29/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 507a26290143bd3a5605e3b97b388d4cfeef4112
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985800"
---
# <a name="visual-studio-2017-administrator-guide"></a>Visual Studio 2017 管理者ガイド

エンタープライズ環境では、エンドユーザーにネットワーク共有またはシステム管理ソフトウェアを使用してインストールを配置することが、システム管理者にとって一般的です。 エンタープライズ展開をサポートするために、Visual Studio セットアップ エンジンを設計しました。これは、インストールの既定値を事前に構成し、インストール プロセス中にプロダクト キーを展開し、ロールアウトが成功した後に製品の更新プログラムを管理するために、システム管理者がネットワーク インストールの場所を作成できるようにします。 この管理者ガイドでは、ネットワーク環境でエンタープライズ展開を行うためのシナリオ ベースのガイダンスを示します。

## <a name="deploy-visual-studio-2017-in-an-enterprise-environment"></a>エンタープライズ環境で Visual Studio 2017 を配置する

Visual Studio 2017 をクライアント ワークステーションに配置するには、インストール対象となる各コンピューターが[最小インストール要件](/visualstudio/productinfo/vs2017-system-requirements-vs)を満たしている必要があります。 System Center などのソフトウェアから配置するか、バッチ ファイルから配置するかにかかわらず、一般的に次の手順に従って進めます。

1. ネットワークの場所に [Visual Studio 製品ファイルを含むネットワーク共有を作成](create-a-network-installation-of-visual-studio.md)します。

2. インストールする[ワークロードとコンポーネントを選択](workload-and-component-ids.md)します。

3. 既定のインストール オプションを含む[応答ファイルを作成](automated-installation-with-response-file.md)します。 または、インストールを制御するためにコマンド ライン パラメーターを使用する[インストール スクリプトを作成](use-command-line-parameters-to-install-visual-studio.md)します。

4. 必要に応じて、インストール スクリプトの一部として[ボリューム ライセンスのプロダクト キーを適用](automatically-apply-product-keys-when-deploying-visual-studio.md)し、ユーザーがソフトウェアを個別にアクティブにする必要がないようにします。

5. ネットワーク レイアウトを更新して、[エンドユーザーに製品の更新プログラムを配信するタイミングを制御](controlling-updates-to-visual-studio-deployments.md)します。

6. 必要に応じて、レジストリ キーを設定し、[クライアント ワークステーション上にキャッシュされる内容を制御](set-defaults-for-enterprise-deployments.md)します。

7. 任意の配置技術を使用して、前の手順で生成したスクリプトをターゲットの開発者ワークステーションで実行します。

8. 手順 1 で使用したコマンドを定期的に実行して更新されたコンポーネントを追加し、Visual Studio の[最新の更新プログラムを適用してネットワークの場所を更新](update-a-network-installation-of-visual-studio.md)します。

> [!IMPORTANT]
> ネットワーク共有からのインストールは、出所のソースの場所を "記憶" します。 これは、クライアント マシンの修復に、クライアントのインストール元のネットワーク共有に戻る必要があることを意味します。 ネットワークの場所は、Visual Studio 2017 クライアントが組織で実行されると予想される有効期間に合わせて配置されるよう慎重に選択してください。

## <a name="use-visual-studio-tools"></a>Visual Studio Tools を使用する

クライアント コンピューターに[インストールされている Visual Studio インスタンスを検出して管理する](tools-for-managing-visual-studio-instances.md)ために役立つ複数のツールが用意されています。

> [!TIP]
> 管理者のガイドのドキュメントに加えて、Visual Studio 2017 セットアップの情報が、「[Heath Stewart のブログ](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)」に多く掲載されています。

## <a name="specify-customer-feedback-settings"></a>顧客フィードバック設定を指定する

既定では、Visual Studio をインストールすると、カスタマー フィードバックが有効になります。 グループ ポリシーを有効にするとき、個々のコンピューターで顧客フィードバックを無効にするように Visual Studio を構成することができます。 これを行うには、次のキーでレジストリ ベースのポリシーを設定します。

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

エントリ = **OptIn**

値 = (DWORD)
* **0**: オプトアウト
* **1**: オプトイン

顧客フィードバックの設定について詳しくは、「[Visual Studio カスタマー エクスペリエンス向上プログラム](../ide/visual-studio-experience-improvement-program.md)」ページをご覧ください。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
  * [ワークロードとコンポーネント ID のリファレンス](workload-and-component-ids.md)
* [Visual Studio のネットワーク ベース インストールを作成する](create-a-network-installation-of-visual-studio.md)
  * [Visual Studio オフライン インストールに必要な証明書をインストールする](install-certificates-for-visual-studio-offline.md)
* [応答ファイルで Visual Studio を自動化する](automated-installation-with-response-file.md)
* [Visual Studio の展開時にプロダクト キーを自動的に適用する](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Visual Studio のエンタープライズ展開に既定値を設定する](set-defaults-for-enterprise-deployments.md)
* [パッケージ キャッシュの無効化または移動](disable-or-move-the-package-cache.md)
* [Visual Studio のネットワーク ベース インストールを更新する](update-a-network-installation-of-visual-studio.md)
* [Visual Studio 配置の更新プログラムを制御する](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio インスタンスの検出および管理用のツール](tools-for-managing-visual-studio-instances.md)
