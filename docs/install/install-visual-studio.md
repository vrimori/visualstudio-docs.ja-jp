---
title: "Visual Studio 2017 のインストール | Microsoft Docs"
description: "Visual Studio をインストールする方法について、ステップ バイ ステップで説明します。"
ms.custom: 
ms.date: 07/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 24fa929fd241a8f9baec5eaa514db459ed014a60
ms.openlocfilehash: 03c763cb4558c5948424b1f0cdc9f077594c12e7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="install-visual-studio-2017"></a>Visual Studio 2017 のインストール
ここでは、Visual Studio の新しいインストール方法について説明します。 最新バージョンでは、必要な機能だけを簡単に選んでインストールできるようになりました。 また、Visual Studio の最小フットプリントも減らしているため、以前よりもシステムへの影響が少なくなり、より迅速にインストールできます。

このバージョンの他の新機能については、 [リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)を参照してください。   

インストールの準備ができたら、 各ステップを順に実行していきます。

## <a name="check-system-requirements"></a>システム要件を確認する
作業を始める前に、[システム要件](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs)をチェックして、コンピューターが Visual Studio 2017 をインストールできる状態であることを確認します。

## <a name="download-visual-studio"></a>Visual Studio をダウンロードする
次に、Visual Studio ブートストラップ ファイルをダウンロードします。 これを行うには、以下のボタンをクリックし、必要な Visual Studio 2017 のエディションを選択して、**[保存]**、**[フォルダーを開く]** の順にクリックします。

 > [!div class="button"]
 > [Visual Studio 2017 をダウンロードする](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
<br/>


|         |         |
|---------|---------|
|  ![ビデオのフィルム アイコン](media/video-icon.png "ビデオを見る")  |    Visual Studio ブートストラップ ファイルをダウンロードして、適切な Visual Studio のエディションを選択する方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171)をご覧ください。 |

## <a name="install-the-installer"></a>インストーラーのインストール  
次に、ブートストラップ ファイルを実行して、Visual Studio インストーラーをインストールします。 この新しい軽量インストーラーには、Visual Studio 2017 のインストールとカスタマイズの両方に必要なすべてのものが含まれています。

1.  **[ダウンロード]** フォルダーで、次のいずれかのファイルと一致する、または似ているブートストラップをダブルクリックします。

  * Visual Studio Enterprise の場合は **vs_enterprise.exe**
  * Visual Studio Professional の場合は **vs_professional.exe**
  * Visual Studio Community の場合は **vs_community.exe**  <br><br>

  ユーザー アカウント制御の通知を受信する場合、**[はい]** をクリックします。  

2.  Microsoft の[ライセンス条項](https://www.visualstudio.com/license-terms/)と[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=824704)の確認を求められます。 **[続行]**をクリックします。  

   ![ライセンス条項とプライバシーに関する声明](media/vs2017-privacy-and-license-terms.PNG "Microsoft のライセンス条項とプライバシーに関する声明")  

## <a name="install-workloads"></a>ワークロードのインストール  
 インストーラーがインストールされたら、それを使用して、必要な機能セット (またはワークロード) を選択し、インストールをカスタマイズすることができます。 ここではその方法を説明します。

1.  **[Visual Studio のインストール]** 画面で、必要なワークロードを見つけます。

  ![Visual Studio 2017 セットアップ ダイアログ](media/vs2017-workloads.PNG "Visual Studio ワークロードのインストール")

     たとえば、.NET デスクトップ開発ワークロードを選択します。 これには既定のコア エディターが用意されており、20 を超える言語の基本的なコード編集サポートが含まれ、プロジェクトなしで任意のフォルダーからコードを開いて編集することができます。また、統合ソース コード管理を利用できます。  

2.  必要なワークロード (複数可) を選択したら、**[インストール]** をクリックします。  

    そうすると、ステータス画面が表示され、Visual Studio のインストールの進行状況が示されます。

3.  新しいワークロードとコンポーネントがインストールされたら、**[起動]** をクリックします。

|         |         |
|---------|---------|
|  ![ビデオのフィルム アイコン](media/video-icon.png "ビデオを見る")  |    Visual Studio インストーラーをインストールしてからワークロードをインストールする方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171)をご覧ください。 |

## <a name="install-individual-components"></a>個々のコンポーネントのインストール

Visual Studio のインストールをカスタマイズする際に便利なワークロード機能を使用しない場合は、代わりに個々のコンポーネントをインストールすることができます。 これを行うには、Visual Studio インストーラーから **[個別のコンポーネント]** オプションをクリックして、必要なものを選択してから画面の指示に従います。

  ![Visual Studio 2017 - 個々のコンポーネントのインストール](media/vs2017-components.PNG "Visual Studio の個々のコンポーネントのインストール")

  |         |         |
  |---------|---------|
  |  ![ビデオのフィルム アイコン](media/video-icon.png "ビデオを見る")  |   Visual Studio インストーラーを使用して、個々のコンポーネントをインストールする方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171)をご覧ください。 |

## <a name="install-language-packs"></a>言語パックのインストール

既定では、インストーラー プログラムが、最初の実行時にオペレーティング システムの言語の照合を試みます。 選択した言語で Visual Studio 2017 をインストールするには、Visual Studio インストーラーで **[言語パック]** オプションをクリックし、画面の指示に従います。

  ![Visual Studio 2017 - 言語パックのインストール](media/vs2017-languages.PNG "Visual Studio の言語パックのインストール")

  |         |         |
  |---------|---------|
  |  ![ビデオのフィルム アイコン](media/video-icon.png "ビデオを見る")  |   Visual Studio インストーラーを使用して、言語パックをインストールする方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171)をご覧ください。 |

### <a name="change-the-installer-language-from-the-command-line"></a>コマンド ラインかインストーラーの言語を変更する

コマンド ラインからインストーラーを実行して、既定の言語を変更することもできます。 たとえば、`vs_installer.exe --locale en-US` コマンドを実行して、インストーラーを英語で実行するように指定することができます。 この設定は、次回インストーラーを実行したときにも保持されています。 インストーラーでは次の言語トークンがサポートされます。zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru、tr-tr。

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング](troubleshooting-installation-issues.md)」ページにあるトラブルシューティングのヒントをご覧ください。

## <a name="see-also"></a>関連項目  
* [Visual Studio 2017 の変更](modify-visual-studio.md)
* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
* [Visual Studio 2017 管理者ガイド](visual-studio-administrator-guide.md)
  * [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 2017 で問題を報告する方法](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

