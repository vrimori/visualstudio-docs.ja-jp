---
title: "オフライン環境での Visual Studio のインストールに関する特別な考慮事項 | Microsoft Docs"
description: "{{プレースホルダー}}"
ms.date: 05/09/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
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
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: ja-jp
ms.lasthandoff: 05/09/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>オフライン環境での Visual Studio のインストールに関する特別な考慮事項

Visual Studio は、本来、インターネットに接続されているコンピューターからインストールするように設計されています。多くのコンポーネントが定期的に更新されるためです。 しかしながら、いくつかの追加手順を踏めば、インターネットが利用できない環境で Visual Studio を展開できます。

## <a name="create-a-network-installation-layout"></a>ネットワーク インストール レイアウトを作成する
* 詳細については、「[Visual Studio のネットワーク ベース インストールを作成する](create-a-network-installation-of-visual-studio.md)」を参照してください。

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Visual Studio オフライン インストールに必要な証明書をインストールする
Visual Studio セットアップ エンジンでは、信頼されているコンテンツのみがインストールされます。  ダウンロードされるコンテンツの Authenticode 署名を検証し、信頼されていることをインストール前に確認します。  インターネットにアクセスできるコンピューターは、ファイル署名の検証に必要なあらゆる証明書を自動的にダウンロードし、インストールします。  ただし、このような操作は、オフライン環境やインターネットの接続が良くないシステムで作業している場合、不可能になることがあります。  そのような環境で作業するユーザーのために、必要な証明書を事前にインストールする必要があります。  これらの証明書は、オフライン インストールの作成時に、実行コンピューターが "証明書" フォルダーにダウンロードします。

証明書ファイルを手動でダブルクリックし、証明書マネージャー ウィザードを完了することでクライアントに証明書をインストールできます。 パスワードを求められたら、空のままにしてください。

証明書インストールのスクリプト化は次の手順で行います。

1. certmgr.exe をインストール共有にコピーします (`\server\share\vs2017` など)。 `certmgr.exe` は Windows SDK に含まれています。これは_ユニバーサル Windows プラットフォーム開発_ワークロードの任意コンポーネントとしてインストールできます。 (例: `"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. 次のコマンドでバッチ ファイルを作成します。

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. クライアントで管理者コマンド シェルまたは管理者特権プロセスからバッチ ファイルを実行します。

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>`certificates` フォルダーから証明書が自動的にインストールされません。
署名がオンライン環境で検証されるとき、Windows API が利用されて証明書がシステムにダウンロードされ、追加されます。 このプロセスで、証明書が信頼できることと管理者設定で許可されることが確認されます。 ほとんどのオフライン環境では、この検証プロセスを実行できません。 証明書を手動でインストールすることで、証明書が信頼できることと管理者要件に一致することを確認できます。

## <a name="install-visual-studio"></a>Visual Studio のインストール
証明書をインストールしたら、[ここの手順](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation)で Visual Studio の展開をオフラインで続行できます。特別な追加手順はありません。


## <a name="see-also"></a>関連項目
* [Visual Studio のインストール](install-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)

