---
title: Visual Studio 2017 のインストール | Microsoft Docs
description: Visual Studio をインストールする方法について、ステップ バイ ステップで説明します。
ms.custom: ''
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51543921049082b4fca5a04f20b8adfc753d8112
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283446"
---
# <a name="install-visual-studio-2017"></a>Visual Studio 2017 のインストール

ここでは、Visual Studio の新しいインストール方法について説明します。 最新バージョンでは、必要な機能だけを簡単に選んでインストールできるようになりました。 また、Visual Studio の最小フットプリントも減らしているため、以前よりもシステムへの影響が少なくなり、より迅速にインストールできます。

このバージョンの他の新機能については、 [リリース ノート](/visualstudio/releasenotes/vs2017-relnotes)を参照してください。

インストールの準備ができたら、 各ステップを順に実行していきます。

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>手順 1 - コンピューターで Visual Studio の準備ができていることを確認する

Visual Studio のインストールを開始する前に

1. [システム要件](/visualstudio/productinfo/vs2017-system-requirements-vs)を確認します。 これらの要件により、ご利用のコンピューターが Visual Studio 2017 に対応しているかどうかを確認できます。
2. 最新の Windows 更新プログラムを適用します。 これらの更新プログラムにより、Visual Studio の最新のセキュリティ更新プログラムと必要なシステム コンポーネントの両方がコンピューターにインストールされます。
3. 再起動します。 この再起動により、Visual Studio のインストールの際に妨げとなる、保留中のインストールや更新プログラムがないようにします。
4. 記憶域を解放します。 ディスク クリーンアップ アプリを実行するなどして、%SystemDrive% から不要なファイルとアプリケーションを削除します。

Visual Studio 2017 と以前のバージョンの Visual Studio を共存させて実行することについて疑問点があれば、[Visual Studio の互換性の詳細](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases)に関する記事をご覧ください。

## <a name="step-2---download-visual-studio"></a>手順 2 - Visual Studio をダウンロードする

次に、Visual Studio ブートストラップ ファイルをダウンロードします。 これを行うには、以下のボタンをクリックし、必要な Visual Studio 2017 のエディションを選択して、**[保存]**、**[フォルダーを開く]** の順にクリックします。

 > [!div class="button"]
 > [Visual Studio 2017 をダウンロードする](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![ビデオのムービー カメラ アイコン](media/video-icon.png "ビデオを見る")  |    Visual Studio ブートストラップ ファイルをダウンロードして、適切な Visual Studio のエディションを選択する方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171)をご覧ください。 |

## <a name="step-3---install-the-visual-studio-installer"></a>手順 3 - Visual Studio インストーラーをインストールする

次に、ブートストラップ ファイルを実行して、Visual Studio インストーラーをインストールします。 この新しい軽量インストーラーには、Visual Studio 2017 のインストールとカスタマイズの両方に必要なすべてのものが含まれています。

1. **[ダウンロード]** フォルダーで、次のいずれかのファイルと一致する、または似ているブートストラップをダブルクリックします。

  * Visual Studio Enterprise の場合は **vs_enterprise.exe**
  * Visual Studio Professional の場合は **vs_professional.exe**
  * Visual Studio Community の場合は **vs_community.exe**  <br><br>

  ユーザー アカウント制御の通知を受信する場合、**[はい]** をクリックします。

2. Microsoft の[ライセンス条項](https://visualstudio.microsoft.com/license-terms/)と[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=824704)の確認を求められます。 **[続行]** をクリックします。

   ![ライセンス条項とプライバシーに関する声明](media/vs2017-privacy-and-license-terms.PNG "Microsoft のライセンス条項とプライバシーに関する声明")

## <a name="step-4---select-workloads"></a>手順 4 - ワークロードを選択する

インストーラーがインストールされたら、それを使用して、必要な機能セット (またはワークロード) を選択し、インストールをカスタマイズすることができます。 ここではその方法を説明します。

1. **[Visual Studio のインストール]** 画面で、必要なワークロードを見つけます。

 ![Visual Studio 2017 の設定ダイアログからワークロードを選択する](../install/media/install-visual-studio-community.png)

     たとえば、".NET デスクトップ開発" ワークロードを選択します。 これには既定のコア エディターが用意されており、20 を超える言語の基本的なコード編集サポートが含まれ、プロジェクトなしで任意のフォルダーからコードを開いて編集することができます。また、統合ソース コード管理を利用できます。

2. 必要なワークロード (複数可) を選択したら、**[インストール]** をクリックします。

    そうすると、ステータス画面が表示され、Visual Studio のインストールの進行状況が示されます。

3. 新しいワークロードとコンポーネントがインストールされたら、**[起動]** をクリックします。

> [!TIP]
> インストール後いつでも、最初にインストールしなかったワークロードまたはコンポーネントをインストールできます。 Visual Studio を開いている場合は、**[ツール]** > **[ツールと機能を取得]** に移動すると、Visual Studio インストーラーが開きます。 または、スタート メニューから **Visual Studio インストーラー**を開きます。 そこから、インストールするワークロードまたはコンポーネントを選択し、**[変更]** をクリックします。

|         |         |
|---------|---------|
|  ![ビデオのムービー カメラ アイコン](media/video-icon.png "ビデオを見る")  |    Visual Studio インストーラーをインストールしてからワークロードをインストールする方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171)をご覧ください。 |

## <a name="step-5---select-individual-components-optional"></a>手順 5 - 個々のコンポーネントを選択する (省略可能)

Visual Studio のインストールをカスタマイズする際にワークロード機能を使用しない場合は、代わりに個々のコンポーネントをインストールできます。 個別のコンポーネントを選択するには、Visual Studio インストーラーから **[個別のコンポーネント]** オプションをクリックして、必要なものを選択してから画面の指示に従います。

  ![Visual Studio 2017 - 個々のコンポーネントのインストール](media/vs2017-components.PNG "Visual Studio の個々のコンポーネントのインストール")

  |         |         |
  |---------|---------|
  |  ![ビデオのムービー カメラ アイコン](media/video-icon.png "ビデオを見る")  |   Visual Studio インストーラーを使用して、個々のコンポーネントをインストールする方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171)をご覧ください。 |

## <a name="step-6---install-language-packs-optional"></a>手順 6 - 言語パックをインストールする (省略可能)

既定では、インストーラー プログラムが、最初の実行時にオペレーティング システムの言語の照合を試みます。 選択した言語で Visual Studio 2017 をインストールするには、Visual Studio インストーラーで **[言語パック]** オプションをクリックし、画面の指示に従います。

  ![Visual Studio 2017 - 言語パックのインストール](media/vs2017-languages.PNG "Visual Studio の言語パックのインストール")

  |         |         |
  |---------|---------|
  |  ![ビデオのムービー カメラ アイコン](media/video-icon.png "ビデオを見る")  |   Visual Studio インストーラーを使用して、言語パックをインストールする方法については、[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171)をご覧ください。 |

### <a name="change-the-installer-language-from-the-command-line"></a>コマンド ラインかインストーラーの言語を変更する

コマンド ラインからインストーラーを実行して、既定の言語を変更することもできます。 たとえば、`vs_installer.exe --locale en-US` コマンドを実行して、インストーラーを英語で実行するように指定することができます。 この設定は、次回インストーラーを実行したときにも保持されています。 インストーラーでは次の言語トークンがサポートされます。zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru、tr-tr。

## <a name="step-7---change-the-installation-location-optional"></a>手順 7 - インストール場所の変更 (省略可能)

**15.7 の新機能**: システム ドライブ上の Visual Studio のインストール フットプリントを小さくできるようになりました。 ダウンロード キャッシュ、共有コンポーネント、SDK、およびツールを別のドライブに移動して、Visual Studio を最速で実行できるドライブで維持できます。

  ![Visual Studio 2017 - インストール場所を変更する](media/installation-options-by-location.png "インストール場所を変更する")

詳細については、「[Change installation locations in Visual Studio](change-installation-locations.md)」 (Visual Studio のインストール場所を変更する) ページを参照してください。

## <a name="step-8---start-developing"></a>手順 8 - 開発を始める

1. Visual Studio のインストールが完了したら **[起動]** をクリックして、[Visual Studio を使用した開発を開始](../ide/get-started-developing-with-visual-studio.md)します。

2. **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。

3. プロジェクトの種類を選択します。 <br><br>
   たとえば、[C++ アプリをビルドする](../ide/getting-started-with-cpp-in-visual-studio.md)には、**[インストール済み]** をクリックし、**[Visual C++]** を展開して、ビルドする C++ プロジェクトの種類を選択します。 <br><br>
   [C# アプリをビルドする](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)には、**[インストール済み]** をクリックし、**[Visual C#]** を展開して、ビルドする C# プロジェクトの種類を選択します。

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://visualstudio.microsoft.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio 2017 の更新](update-visual-studio.md)
* [Visual Studio 2017 の変更](modify-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
* [Visual Studio 2017 のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio 2017 管理者ガイド](visual-studio-administrator-guide.md)
  * [コマンド ライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [コンテナーにビルド ツールをインストールする](build-tools-container.md)
