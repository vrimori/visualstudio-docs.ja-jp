---
title: Visual Studio 管理者ガイド |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: b8f25b995079aeedca262dedd62b2f9c880efb52
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879214"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Administrator Guide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。、 [Visual Studio 2017 管理者ガイド](/visualstudio/install/visual-studio-administrator-guide)します。

各ターゲット コンピューターが満たしている限り、ネットワーク上の Visual Studio 2015 を展開することができます、[最小インストール要件](http://www.microsoft.com/visualstudio/eng/products/2013-editions)します。 /Layout スイッチを使用して、インストール ファイルを実行してネットワーク共有を作成することができます (上の説明に従って、[の Visual Studio オフライン インストールを作成](../install/create-an-offline-installation-of-visual-studio.md)ページ) し、ローカル コンピューターからネットワーク共有にコピーします。 ISO を使用している場合、ISO をマウントする共有し、ISO をネットワーク共有にコピーまたはできます。  
  
 ネットワーク共有からのインストールは、出所のソースの場所を記憶します。 これは、クライアント マシンの修復に、クライアントのインストール元のネットワーク共有に戻る必要があることを意味します。 ネットワークの場所は、Visual Studio 2015 クライアントが組織で実行されると予想される有効期間に合わせて配置されるよう慎重に選択してください。  
  
## <a name="detection-and-servicing-keys"></a>検出キーおよびサービス キー  
 レジストリの検出サブキーを使用して、Visual Studio 製品がコンピューターに既にインストールされているかどうかを確認できます。 自動化された展開で検出キーを使用して、インストールを続行するために必要かどうかを確認します。  参照してください[システム要件の検出](../extensibility/internals/detecting-system-requirements.md)[システム要件の検出]。  
  
## <a name="avoiding-reboots"></a>再起動の回避  
 Visual Studio を配置する前に Visual Studio の適切な前提条件を確認することによって、再起動を減らすことができます。 .NET framework では、最初に、.NET Framework 4.6 をインストールせずに Visual Studio 2015 を展開する場合、Windows 8 を実行しているコンピューターを再起動する必要があります。  
  
 Windows および Android デバイスのエミュレーションでは、Windows 機能の HYPER-V がオンになっていないと、コンピューターの再起動が必要になる場合があります。 Web 開発では、Windows 機能の Web サーバーがオンになっていないと、コンピューターの再起動が必要になる場合があります。 Office の開発では、Windows 機能の Windows Identify Foundation がオンになっていないと、コンピューターの再起動が必要になる場合があります。 Web 開発では、Windows 機能の Web Server がオンになっていないと、コンピューターの再起動が必要になる場合があります。 Office の開発では、Windows 機能の Windows Identify Foundation がオンになっていないと、コンピューターの再起動が必要になる場合があります。 Windows 機能の検出とインストールを自動化する方法の詳細については、「 [Windows Server 2008 R2 の Server Core インストールを実行しているサーバーにサーバー ロールをインストールする](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx)」を参照してください。  
  
## <a name="error-return-codes"></a>エラー リターン コード  
 次の表に重要なエラー コードを示します。 これらのエラー コードは、再起動が必要かどうか、インストールが成功したかどうかを判断するために自動化で使用できます。 エラー コードを受信する場合のトラブルシューティングの手順を検討してください、 [Visual Studio のインストール](../install/install-visual-studio-2015.md)ページ。  
  
|セットアップの状態|再起動は不要|再起動が必要|説明|  
|------------------|--------------------------|----------------------|-----------------|  
|成功|0x00000000 [0]|0x00000bc2 [3010]|インストールは成功しました。|  
|ブロック|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|報告するブロックが "再起動の保留中" だけの場合、戻り値は "不完全-再起動が必要" の値 (0x80048bc7) です。|  
|キャンセル|0x00000642 [1602]|0x80048642 [-2147187134]|再起動値が返されると、結果コードは 1602 です。|  
|不完全-再起動が必要|N/A|0x80048bc7 [-2147185721]|インストールを続行するには再起動が必要です。|  
|失敗|0x00000643 [1603]|0x80048643 [-2147187133]|再起動値が返されると、結果コードは 1603 です。|  
  
## <a name="interactive-administrator-installer"></a>対話型の管理者のインストーラー  
 Visual Studio のインストールに対話型のインストーラーを作成する場合、Visual Studio インストーラーから進行状況を表示できます。 Visual Studio 2015 インストーラーは、オープン ソースの Windows インストーラー XML (WiX) チェーン元テクノロジ ("書き込み" とも呼ばれる) に基づいて構築されます。 書き込みテクノロジは、burn と netfx4 の 2 つの通信プロトコルをサポートします。 簡単なリファレンスについては、 [wixtoolset.org](http://wixtoolset.org/)にある ExePackage 要素に関するドキュメント内のプロトコル属性の説明を参照してください。このプロトコル属性の WiX オープン ソースの実装の確認は、統合に必要な場合があります。  
  
## <a name="controlling-what-is-installed"></a>インストール内容の制御  
 エンド ユーザーによるインストール内容を制御する場合、管理者ファイルのインストールとコマンド ラインの 2 つのオプションがあります。 エンド ユーザーが Visual Studio インストーラー エクスペリエンスから選択できる内容を制限することが目的の場合は、管理者ファイルのインストールを選択できます、 初期構成を作成しつつ、エンド ユーザーが独自の Visual Studio インストーラー エクスペリエンスから選択できるようにする場合、コマンド ラインのパラメーターを選択します。  
  
 管理者ファイル エクスペリエンスの詳細については、「 [How to: Create and Run an Unattended Installation of Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) 」および「 [How to: Automatically apply product keys when deploying Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)」を参照してください。  コマンドライン制御の詳細については、次を参照してください。、 [Visual Studio をインストールするコマンド ライン パラメータを使用して](../install/use-command-line-parameters-to-install-visual-studio.md)ページ。  
  
## <a name="specifying-customer-feedback-settings"></a>顧客フィードバック設定の指定  
 既定では、Visual Studio をインストールすると、カスタマー フィードバックが有効になります。 次のレジストリ キーの値を文字列 "0" に変更することで、個々のコンピューターで顧客からのカスタマー フィードバックを無効にするように Visual Studio を構成できます。  
  
 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
 (たとえば、HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn="0" に変更します)  
  
## <a name="related-topics"></a>関連トピック  
  
|トピック|説明|  
|-----------|-----------------|  
|[方法: Visual Studio の特定のリリースをインストールする](../install/how-to-install-a-specific-release-of-visual-studio.md)|現在のバージョンの特定の構成をインストールする方法について説明します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。|  
|[方法: Visual Studio の無人インストールを作成して実行する](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|インストールする方法について説明します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]無人モードでします。|  
|[方法: Visual Studio の展開時にプロダクト キーを自動的に適用する](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|複数のコンピューターに展開するときに、プロダクト キーを適用する方法について説明します。|  
|[ヘルプ ビューアーの管理者ガイド](../ide/help-viewer-administrator-guide.md)|ネットワーク環境があるか、インターネットへのアクセスがないローカル ヘルプのインストールを管理する方法について説明します。|  
|[Visual Studio のインストール](../install/install-visual-studio-2015.md)|手順については、インストールする方法を説明するトピックへのリンクを提供します。[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。|