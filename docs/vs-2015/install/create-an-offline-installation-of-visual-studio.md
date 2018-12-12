---
title: Visual Studio のオフライン インストールを作成する | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 6d17d8e7e5edcff6913e0046f0b580362cbc4950
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755657"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio のオフライン インストールを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください[低帯域幅または信頼性の低いネットワーク環境での Visual Studio 2017 のインストール](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network)、または[Visual Studio 2017 のネットワーク インストールを作成](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio)と。[オフライン環境で Visual Studio 2017 をインストールするための特別な考慮事項](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment)します。

このページには、インターネットに接続されていないときに、Visual Studio 2015 をインストールする方法について説明します。 ただし、「切断済み」のインストールを実行する必要があります最初に作成するオフライン インストール レイアウトをインターネットに接続されているマシンを使用しています。 これを行う方法を次に示します。  

> [!IMPORTANT]
>  オフラインのコンピューターが Windows 7 SP1 または Windows Server 2008 R2 を実行している場合の特別な指示を参照してください、[オフライン インストールのトラブルシューティング](#BKMK_tshoot)このトピックの「します。  この手順に従う必要があります*する前に*Visual Studio 2015 をインストールします。  

##  <a name="BKMK_Offline"></a> オフライン インストールを作成してインストールする.  

#### <a name="to-create-an-offline-installation-layout"></a>オフライン インストール レイアウトを作成するには  

1.  インストールする Visual Studio のエディションを選択、 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015)ページをダウンロードします。  

2.  ファイル システム上の場所にインストーラーをダウンロードした後に実行"\<実行可能ファイル名 >/layout"。  

     たとえばを実行します。 `vs_enterprise.exe /layout D:\VisualStudio2015`  

     使用して、`/layout`スイッチをほぼすべてのインストール パッケージで、ダウンロード先のコンピューターに適用されるものだけでなくをダウンロードすることができます。 この方法では、どこでもこのインストーラーを実行する必要のあるファイルと、最初にインストールされていないコンポーネントをインストールする場合に便利ですがあります。  

3.  このコマンドを実行した後、オフライン インストール レイアウトを配置するフォルダーを変更することを許可する ダイアログ ボックスが表示されます。   次に、クリックして、**ダウンロード**ボタンをクリックします。  

     というメッセージが表示、パッケージのダウンロードが成功したら、**セットアップ完了です。指定したコンポーネントがすべて正常に取得されました。**  

4.  前に指定したフォルダーを見つけます。 (たとえば、検索 D:\VisualStudio2015。)このフォルダーには、共有の場所にコピーまたはインストール メディアに必要なすべてが含まれています。  

    > [!CAUTION]
    >  現在、Android SDK はオフライン インストール エクスペリエンスをサポートしていません。 Android SDK セットアップ項目をインターネットに接続されていないコンピューターにインストールする場合、インストールが失敗する可能性があります。 詳細については、このトピックの「オフライン インストールのトラブルシューティング」セクションを参照してください。  

5.  ファイルの場所から、またはインストール メディアからインストールを実行します。  

## <a name="updating-an-offline-installation"></a>オフライン インストールの更新  
 マイクロソフトは、Visual Studio 2015 の複数の更新プログラムをリリースしました。 Visual Studio のインストールを更新するから必要なエディションをダウンロードから、 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015)ページをダウンロードします。 次に、新しいオフライン インストール レイアウトを作成するには、このトピックで説明する手順に従うし、それを使用して、Visual Studio 2015 のコピーを更新します。  

##  <a name="BKMK_tshoot"></a> オフライン インストールのトラブルシューティング  
 オフライン インストール キャッシュからオフラインでインストールする際に、一部のコンポーネントとパッケージをインストールできないことを示す警告メッセージが表示される場合があります。 そのようなシナリオで使用可能なソリューションを以下の表に示します。  


|                                                                                       コンポーネントまたはパッケージ                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                   ソリューション                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dotfuscator および Analytics Community Edition 5.19.1 (にインストールされている、Visual Studio の Community、Professional、および Enterprise エディションの**Windows 7 SP1**と**Windows Server 2008 R2**) |                                                                                                                                       オフラインのコンピューターが実行されている場合**Windows 7 SP1**または**Windows Server 2008 R2**、Visual Studio 2015 をインストールする前に、次の手順を実行する必要があります。<br /><br /> 1.CTL ファイルをダウンロードするファイルまたは web サーバーを構成します。<br /><br /> 2.  切断された環境の Microsoft Automatic Update URL をリダイレクトします。<br /><br /> 詳細については、次を参照してください。、[信頼されたルートを構成および許可されない証明書](https://technet.microsoft.com/library/dn265983.aspx)、Microsoft TechNet サイトのページ。                                                                                                                                       |
|                                                                                  Android SDK セットアップ (API レベル)                                                                                   |                                                                        Android SDK (API レベル) パッケージをインストールするには、インターネットに接続する必要があります。 制限付きネットワークを使用している場合は、Visual Studio のインストール時に次の URL へのアクセスを許可する必要があります。<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />プロキシの設定で考えられる問題を解決する方法の詳細については、次を参照してください。、 [Visual Studio 2015 のインストール エラー (Android SDK セットアップ) プロキシの背後にある](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/)ブログの投稿。                                                                         |
|                             Visual Studio の拡張項目テンプレート<br /><br /> Visual Studio 向け GitHub 拡張<br /><br /> PowerShell Tools for Visual Studio                             | Visual Studio 2015 をインストールするときに、インターネット接続があるありません、特殊なオフライン インストール レイアウトを生成するオフライン フィードを使用することができます。 **注:** この特殊なフィードには Visual Studio 2015 の最新の更新プログラムが含まれています。 <br /><br /> 特殊なオフライン フィードを作成するには、次のコマンドを実行します/layout*ドライブ:* \VisualStudio2015/overridefeeduri *xml フィード URL。*<br /><br /> たとえば、Visual Studio 2015 Enterprise の英語版の特別なオフライン フィードの次のように実行します。<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> 好みの言語で特別なオフライン フィードを作成するのに使用できる Url の完全な一覧は、次の表を参照してください。 |

 上記の表に示すように、言語固有特別なオフライン フィードを作成するのに次の Url を使用します。  


|       言語        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| 中国語 (簡体字、中国)  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| では  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         チェコ語         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        ドイツ語         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        英語        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        スペイン語        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        フランス語         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        イタリア語        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       日本語        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        韓国語         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        ポーランド語         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      ポルトガル語       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        ロシア語        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        トルコ語        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>関連項目  
 [Visual Studio のインストール]()