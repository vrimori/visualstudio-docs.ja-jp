---
title: "Visual Studio 管理者ガイド | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
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
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
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
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: c88a932beac964117ac2fd6ffe171bf4256ac706
ms.contentlocale: ja-jp
ms.lasthandoff: 05/08/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Visual Studio 2017 管理者ガイド

エンタープライズ環境では、エンドユーザーにネットワーク共有またはシステム管理ソフトウェアからインストールを配置することが、システム管理者にとって一般的です。 エンタープライズ展開をサポートするために、Visual Studio セットアップ エンジンを設計しました。これは、インストールの既定値を事前に構成し、インストール プロセス中にプロダクト キーを展開し、ロールアウトが成功した後に製品の更新プログラムを管理するために、システム管理者がネットワーク インストールの場所を作成できるようにします。 この管理者ガイドでは、共通のネットワーク環境でエンタープライズ展開を行うためのシナリオ ベースのガイダンスを示します。

## <a name="steps-for-deploying-visual-studio-2017-in-an-enterprise-environment"></a>エンタープライズ環境で Visual Studio 2017 を配置するための手順

Visual Studio 2017 をクライアント ワークステーションに配置するには、インストール対象となる各コンピューターが[最小インストール要件](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)を満たしている必要があります。 System Center などのソフトウェアから配置するか、バッチ ファイルから配置するかにかかわらず、一般的に次の手順に従って進めます。

1. ネットワークの場所に [Visual Studio 製品ファイルを含むネットワーク共有を作成](create-a-network-installation-of-visual-studio.md)します。

2. インストールする[ワークロードとコンポーネントを選択](workload-and-component-ids.md)します。

3. 既定のインストール オプションを含む[応答ファイルを作成](automated-installation-with-response-file.md)します。 または、インストールを制御するためにコマンド ライン パラメーターを使用して、[インストール スクリプトを作成](use-command-line-parameters-to-install-visual-studio.md)します。

4. 必要に応じて、インストール スクリプトの一部として[ボリューム ライセンスのプロダクト キーを適用](automatically-apply-product-keys-when-deploying-visual-studio.md)し、ユーザーがソフトウェアを個別にアクティブにする必要がないようにします。

5. ネットワーク レイアウトを更新して、[エンドユーザーに製品の更新プログラムを配信するタイミングを制御](controlling-updates-to-visual-studio-deployments.md)します。

6. 必要に応じて、レジストリ キーを設定し、[クライアント ワークステーション上にキャッシュされる内容を制御](set-defaults-for-enterprise-deployments.md)します。

7. 任意の配置テクノロジを使用して、前の手順で生成したスクリプトをターゲットの開発者ワークステーションで実行します。

8. 手順 1 で使用したコマンドを定期的に実行して更新されたコンポーネントを追加し、Visual Studio の[最新の更新プログラムを適用してネットワークの場所を更新](update-a-network-installation-of-visual-studio.md)します。

> [!IMPORTANT]
> ネットワーク共有からのインストールは、出所のソースの場所を記憶します。 これは、クライアント マシンの修復に、クライアントのインストール元のネットワーク共有に戻る必要があることを意味します。 ネットワークの場所は、Visual Studio 2017 クライアントが組織で実行されると予想される有効期間に合わせて配置されるよう慎重に選択してください。

## <a name="tools"></a>ツール
クライアント マシンに[インストールされている Visual Studio インスタンスを検出して管理する](tools-for-managing-visual-studio-instances.md)ために役立つ複数のツールが用意されています。

> [!TIP]
> 管理者のガイドのドキュメントに加えて、Visual Studio 2017 セットアップの情報が、「[Heath Stewart のブログ](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)」に豊富に含まれています。

## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [オフライン環境での Visual Studio のインストール](install-visual-studio-in-offline-environment.md)
* [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
* [Visual Studio 2017 で問題を報告する](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

