---
title: "Visual Studio 2017 RC のインストール | Microsoft Docs"
description: "Visual Studio をインストールする方法について、ステップ バイ ステップで説明します。"
ms.custom: 
ms.date: 11/18/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio Preview
- install Visual Studio
- installing Visual Studio
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
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 997a1e0966c5e08314c616dba76842120ab50d63

---
# <a name="install-visual-studio-2017-rc"></a>Visual Studio 2017 RC のインストール
ここでは、Visual Studio の新しいインストール方法について説明します。 最新バージョンでは、必要な機能のみをより簡単に選択してインストールできるようになりました。Visual Studio の最小フットプリントが縮小されたことにより、従来よりもさらにすばやくインストールでき、システムへの影響が小さくなります。  

 RC の他の新機能については、 [リリース ノート](https://www.visualstudio.com/news/releasenotes/vs15-relnotes)を参照してください。 また、新しくなったインストール エクスペリエンスの詳細については、[Visual Studio インストーラーの処理速度と効率性の向上](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)および[影響の少ない Visual Studio インストールの詳細](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)に関するブログ投稿を参照してください。  

 インストールの準備ができたら、 各ステップを順に実行していきます。 では、始めましょう。  

## <a name="install-the-installer"></a>インストーラーのインストール  
 Visual Studio 2017 RC をダウンロードして、ブートストラップ ファイルを取得します。このファイルを実行すると、新しいライトウェイト インストーラーがインストールされます。 この新しいインストーラーには、インストールのカスタマイズに必要なすべてのものが含まれています。  

> [!IMPORTANT]
> ご使用のコンピューターに Visual Studio 2017 のプレビュー リリースがインストールされている場合は、Visual Studio 2017 RC をインストールする前に削除するよう求められます。

1.  [Visual Studio Enterprise 2017 RC をダウンロード](https://www.visualstudio.com/vs/visual-studio-2017-rc/)して、**[保存]** をクリックします。  次に、**ダウンロード** フォルダーから `vs_Enterprise.exe` ファイルを実行します。  

     ユーザー アカウント制御の通知を受信する場合、**[はい]** をクリックします。  

2.  Microsoft の[ライセンス条項](https://www.visualstudio.com/support/legal/mt591984)と[プライバシーに関する声明](https://www.visualstudio.com/dn948229)の確認を求められます。 **[インストール]** をクリックして続行します。  

  ![ライセンス条項とプライバシーに関する声明](media/01-installingdev15prev4-licensetermsandprivacystatement.png "Microsoft のライセンス条項とプライバシーに関する声明")  

3.  インストールの進行状況を示すいくつかのステータス画面が表示されます。 インストールが終了したら、次は、必要な機能セット (ワークロード) を選択します。

## <a name="install-workloads"></a>ワークロードのインストール  
 これで、ワークロードを使用して、インストールをカスタマイズできます。 必要なワークロードを&1; つ以上選択します。各ワークロードには、好みのプログラミング言語またはプラットフォームに必要な機能が含まれています。  

 取得方法は次のとおりです。  

1.  **[Visual Studio のインストール]** 画面で、必要なワークロードを見つけます。  

  ![Visual Studio 2017 RC セットアップ ダイアログ](../ide/media/willow1.png "Visual Studio 2017 のインストール")

     たとえば、.NET デスクトップ開発ワークロードを選択します。 これには既定のコア エディターが用意されており、20 を超える言語の基本的なコード編集サポートが含まれ、プロジェクトなしで任意のフォルダーからコードを開いて編集することができます。また、統合ソース コード管理を利用できます。  

2.  必要なワークロード (複数可) を選択したら、**[インストール]** をクリックします。  

    そうすると、ステータス画面が表示され、Visual Studio のインストール状況が示されます。

3.  新しいワークロードとコンポーネントがインストールされたら、**[起動]** をクリックします。

## <a name="install-individual-components"></a>個々のコンポーネントのインストール

便利なワークロード機能を使用せずに Visual Studio のインストールをカスタマイズする場合は、Visual Studio インストーラーで **[個々のコンポーネント]** オプションをクリックし、必要なものを選択して、画面の指示に従います。

  ![Visual Studio 2017 - 個々のコンポーネントのインストール](media/vs2017install-IndividualComponents.PNG "Visual Studio の個々のコンポーネントのインストール")

## <a name="install-language-packs"></a>言語パックのインストール

選択した言語で Visual Studio 2017 RC をインストールするには、Visual Studio インストーラーで **[言語パック]** オプションをクリックし、画面の指示に従います。

  ![Visual Studio 2017 - 言語パックのインストール](media/vs2017install-LanguagePacks.PNG "Visual Studio の言語パックのインストール")

### <a name="change-the-installer-language"></a>インストーラーの言語の変更

既定では、インストーラー プログラムが、最初の実行時にオペレーティング システムの言語の照合を試みます。 インストーラーはこの設定を記憶します。 コマンド ラインからインストーラーを実行することで、この設定を変更できます。 たとえば、`vs_installer.exe --locale en-US` を実行して、インストーラーを英語で実行するように指定することができます。 この設定は記憶され、インストーラーの次回の実行時に使用されます。 インストーラーでは、zh-CN、zh-TW、cs-CZ、en-US、fr-FR、de-DE、it-IT、ja-JP、ko-KR、pl-PL、pt-BR、ru-RU、es-ES、tr-TR という言語トークンがサポートされます。


  > [!IMPORTANT]
  > Visual Studio 2017 RC は一般に運用環境での使用がサポートされていますが、インストール UI で "プレビュー" とマークされているワークロードやコンポーネントは運用環境での使用がサポートされていません。

## <a name="see-also"></a>関連項目  
* [Visual Studio 2017 RC の変更](modify-visual-studio.md)
* [Visual Studio 2017 RC のアンインストール](uninstall-visual-studio.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [Visual Studio 2017 で問題を報告する方法](../ide/how-to-report-a-problem-with-visual-studio-2017.md)



<!--HONumber=Feb17_HO4-->


