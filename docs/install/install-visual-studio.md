---
title: "Visual Studio 2017 のインストール | Microsoft Docs"
description: "Visual Studio をインストールする方法について、ステップ バイ ステップで説明します。"
ms.custom: 
ms.date: 04/03/2017
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
ms.openlocfilehash: 47688935cec36db174c3a0c424b1705ae47c6118
ms.lasthandoff: 04/03/2017

---
# <a name="install-visual-studio-2017"></a>Visual Studio 2017 のインストール
ここでは、Visual Studio の新しいインストール方法について説明します。 最新バージョンでは、必要な機能のみをより簡単に選択してインストールできるようになりました。Visual Studio の最小フットプリントが縮小されたことにより、従来よりもさらにすばやくインストールでき、システムへの影響が小さくなります。  

 他の新機能については、 [リリース ノート](https://www.visualstudio.com/news/releasenotes/vs15-relnotes)を参照してください。 また、新しくなったインストール エクスペリエンスの詳細については、[Visual Studio インストーラーの処理速度と効率性の向上](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)および[影響の少ない Visual Studio インストールの詳細](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)に関するブログ投稿を参照してください。  

 インストールの準備ができたら、 各ステップを順に実行していきます。 では、始めましょう。  

## <a name="install-the-installer"></a>インストーラーのインストール  
 Visual Studio 2017 をダウンロードして、ブートストラップ ファイルを取得します。このファイルを実行すると、新しいライトウェイト インストーラーがインストールされます。 この新しいインストーラーには、インストールのカスタマイズに必要なすべてのものが含まれています。  

> [!IMPORTANT]
> ご使用のコンピューターに Visual Studio 2017 のプレビュー リリースがインストールされている場合は、Visual Studio 2017 をインストールする前に削除するよう求められます。

1.  **[Visual Studio 2017 をダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)**して **[保存]** をクリックします。 次に、**ダウンロード** フォルダーで、選択したエディションのブートストラップ ファイルを実行します。

  * Visual Studio Enterprise の場合は **vs_enterprise.exe**
  * Visual Studio Professional の場合は **vs_professional.exe**
  * Visual Studio Community の場合は **vs_community.exe**  <br><br>

  ユーザー アカウント制御の通知を受信する場合、**[はい]** をクリックします。  

2.  Microsoft の[ライセンス条項](https://www.visualstudio.com/license-terms/)と[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=824704)の確認を求められます。 **[インストール]** をクリックして続行します。  

   ![ライセンス条項とプライバシーに関する声明](media/vs2017-privacy-and-license-terms.PNG "Microsoft のライセンス条項とプライバシーに関する声明")  

3.  インストールの進行状況を示すいくつかのステータス画面が表示されます。 インストールが終了したら、次は、必要な機能セット (ワークロード) を選択します。

## <a name="install-workloads"></a>ワークロードのインストール  
 これで、ワークロードを使用して、インストールをカスタマイズできます。 必要なワークロードを 1 つ以上選択します。各ワークロードには、好みのプログラミング言語またはプラットフォームに必要な機能が含まれています。  

 取得方法は次のとおりです。  

1.  **[Visual Studio のインストール]** 画面で、必要なワークロードを見つけます。  

  ![Visual Studio 2017 セットアップ ダイアログ](media/vs2017-workloads.PNG "Visual Studio 2017 のインストール")

     たとえば、.NET デスクトップ開発ワークロードを選択します。 これには既定のコア エディターが用意されており、20 を超える言語の基本的なコード編集サポートが含まれ、プロジェクトなしで任意のフォルダーからコードを開いて編集することができます。また、統合ソース コード管理を利用できます。  

2.  必要なワークロード (複数可) を選択したら、**[インストール]** をクリックします。  

    そうすると、ステータス画面が表示され、Visual Studio のインストール状況が示されます。

3.  新しいワークロードとコンポーネントがインストールされたら、**[起動]** をクリックします。

## <a name="install-individual-components"></a>個々のコンポーネントのインストール

便利なワークロード機能を使用せずに Visual Studio のインストールをカスタマイズする場合は、Visual Studio インストーラーで **[個々のコンポーネント]** オプションをクリックし、必要なものを選択して、画面の指示に従います。

  ![Visual Studio 2017 - 個々のコンポーネントのインストール](media/vs2017-workloads.PNG "Visual Studio の個々のコンポーネントのインストール")

## <a name="install-language-packs"></a>言語パックのインストール

選択した言語で Visual Studio 2017 をインストールするには、Visual Studio インストーラーで **[言語パック]** オプションをクリックし、画面の指示に従います。

  ![Visual Studio 2017 - 言語パックのインストール](media/vs2017-languages.PNG "Visual Studio の言語パックのインストール")

### <a name="change-the-installer-language"></a>インストーラーの言語の変更

既定では、インストーラー プログラムが、最初の実行時にオペレーティング システムの言語の照合を試みます。 インストーラーはこの設定を記憶します。 コマンド ラインからインストーラーを実行することで、この設定を変更できます。 たとえば、`vs_installer.exe --locale en-US` コマンドを実行して、インストーラーを英語で実行するように指定することができます。 この設定は、次回インストーラーを実行したときにも保持されています。 インストーラーでは、zh-CN、zh-TW、cs-CZ、en-US、fr-FR、de-DE、it-IT、ja-JP、ko-KR、pl-PL、pt-BR、ru-RU、es-ES、tr-TR という言語トークンがサポートされます。

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、サポート技術情報の記事「[Visual Studio 2017 で発生するインストールおよびアップグレード エラーのトラブルシューティング](https://support.microsoft.com/help/4015967/troubleshooting-visual-studio-2017-installation-and-upgrade-failures)」にあるトラブルシューティングのヒントを参照してください。

## <a name="see-also"></a>関連項目  
* [Visual Studio 2017 の変更](modify-visual-studio.md)
* [Visual Studio 2017 のアンインストール](uninstall-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [Visual Studio 2017 で問題を報告する方法](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

