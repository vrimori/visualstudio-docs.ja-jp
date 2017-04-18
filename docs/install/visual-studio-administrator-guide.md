---
title: "Visual Studio 管理者ガイド | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
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
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: fb7a87b720ad29252c602d9be5b958d8417ab93e
ms.lasthandoff: 04/03/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Visual Studio 2017 の管理者ガイド

 Visual Studio をネットワークに配置するには、インストール対象となる各コンピューターが[最小インストール要件](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)を満たしている必要があります。

 System Center などのソフトウェアから配置するか、バッチ ファイルから配置するかにかかわらず、一般的に次の手順に従って進めます。

1. ネットワークの場所に [Visual Studio 製品レイアウトをキャッシュ](create-an-offline-installation-of-visual-studio.md)します。

2. インストールする[ワークロードとコンポーネントを選択](workload-and-component-ids.md)します。

3. インストールを制御するために選択した項目とその他のコマンド ライン パラメーターを使用して、[インストール スクリプトを作成](use-command-line-parameters-to-install-visual-studio.md)します。

4. 必要に応じて、インストール スクリプトの一部として[ボリューム ライセンスのプロダクト キーを適用](automatically-apply-product-keys-when-deploying-visual-studio.md)し、ユーザーがソフトウェアを個別にアクティブにする必要がないようにします。

5. 任意の配置技術を使用して、前の手順で生成したスクリプトをターゲットの開発者ワークステーションで実行します。

6. 手順 1 で使用したコマンドを定期的に実行して更新されたコンポーネントを追加し、Visual Studio の最新の更新プログラムを適用してネットワークの場所を更新します。

> [!IMPORTANT]
>  ネットワーク共有からのインストールは、出所のソースの場所を記憶します。 これは、クライアント マシンの修復に、クライアントのインストール元のネットワーク共有に戻る必要があることを意味します。 ネットワークの場所は、Visual Studio 2017 クライアントが組織で実行されると予想される有効期間に合わせて配置されるよう慎重に選択してください。

## <a name="tools"></a>ツール

 クライアント コンピューターにインストールされている Visual Studio インスタンスを検出して管理するために役立つ複数のツールが用意されています。

* [VSWhere](https://github.com/microsoft/vswhere): Visual Studio のインストール済みインスタンスから主要な Visual Studio ツールの場所を見つけるために役立つ、C++ の実行可能ファイルです。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): セットアップ構成 API を使用して Visual Studio のインストール済みインスタンスを識別する PowerShell スクリプトです。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): セットアップ構成 API を使用して既存のインストールを照会する方法を示す C# と C++ のサンプルです。

さらに、[セットアップ構成 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) は、Visual Studio インスタンスを問い合わせるために独自のユーティリティを構築する開発者向けのインターフェイスを提供します。

>[!TIP]
>Visual Studio 2017 のインストールの詳細については、[Heath Stewart のブログ記事](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/)を参照してください。


## <a name="see-also"></a>関連項目
* [Visual Studio 2017 のインストール](install-visual-studio.md)
* [Visual Studio 2017 のオフライン インストーラーを作成する](create-an-offline-installation-of-visual-studio.md)
* [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 で問題を報告する](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

