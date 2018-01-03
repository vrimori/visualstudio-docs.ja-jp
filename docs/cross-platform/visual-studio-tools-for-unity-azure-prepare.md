---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、準備 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7554380435c77750eb48a5ce261cc0a2b3885ccd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="prepare-the-development-environment"></a>開発環境を準備する

Unity で Azure Mobile Client SDK を利用するには、いくつかの前提条件があります。

## <a name="download-and-install-unity-2017"></a>Unity 2017 をダウンロードし、インストールする

Unity 2017.1 以上が必要です。 無料の Personal プランを含むすべての Unity プランがこのチュートリアルの対象となります。 https://store.unity.com/ から Unity をダウンロードします。

## <a name="download-and-install-visual-studio-2017"></a>Visual Studio 2017 をダウンロードし、インストールする

このチュートリアルを利用するには、Visual Studio 2017 15.3 以上と Unity によるゲーム開発ワークロードが必要です。 Community 版も含め、あらゆる版の Visual Studio 2017 がこのチュートリアルの対象となります。

1. https://www.visualstudio.com/ で Visual Studio 2017 をダウンロードします。

2. Visual Studio 2017 をインストールし、**Unity によるゲーム開発**ワークロードが有効になっていることを確認します。

 ![Unity ワークロードを選択する](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Visual Studio 2017 が既にインストールされている場合、Visual Studio インストーラーを実行すると、ワークロードを表示し、変更できます。

## <a name="create-a-new-3d-unity-project"></a>新しい 3D Unity プロジェクトを作成する

Unity を起動し、新しい 3D プロジェクトを作成します。

![新しい Unity プロジェクトを作成する](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>スクリプト エディターを Visual Studio Preview 2017 に設定する

Visual Studio 2017 が Unity の外部スクリプト エディターとして既に設定されている場合がありますが、15.3 プレビュー版が選択されていることを確認することが大切です。

1. Unity の **[Edit]** メニューから、**[Edit]、[Preferences...]** の順に選択します。

  ![[Preferences] メニューを開く](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Unity の [Preferences] ウィンドウが開いたら、左側にある **[External Tools]** タブを選択します。

3. **[External Script Editor]** ドロップダウン メニューで、**[Visual Studio 2017]** を選択します。

  ![外部スクリプト エディターを設定する](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Unity スクリプティング ランタイムを .NET 4.6 に変更する
このチュートリアルでは、Azure Mobile Client SDK とその依存関係を利用する目的で .NET 4.6 が必要になります。

1. Unity の **[File]** メニューから、**[File]、[Build Settings...]** の順に選択します。

  ![ビルド設定を開く](media/vstu_azure-prepare-dev-environment-image4.png)

2. **[Player Settings...]** ボタンをクリックします。

  ![プレーヤー設定を開く](media/vstu_azure-prepare-dev-environment-image5.png)

3. Unity の [Inspector] ウィンドウで [Player Settings...] を開きます。 **[Configuration]** 見出しの下で、**[Scripting Runtime Version]** ドロップダウンをクリックし、**[Experimental (.NET 4.6 Equivalent)]** を選択します。 ダイアログが開き、Unity を再起動するように求められます。 **[Restart]** を選択します。

  ![[.NET 4.6] を選択する](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>System.Net.Http.dll に参照を追加する

Unity のスクリプティング ランタイムに .NET 4.6 Equivalent を選択すると、System.Net.Http パッケージを使用できます。このパッケージは Azure Mobile Client SDK で必要になります。 DLL ファイルは Unity に含まれていますが、使用するには参照を追加する必要があります。

1. Unity エディターの [Project] ウィンドウで、**[Assets]** フォルダーを**右クリック**し、**[Show in Explorer]** を選択します。

  ![エクスプローラーで [Assets] フォルダーを表示する](media/vstu_azure-prepare-dev-environment-image7.png)

2. エクスプローラー ウィンドウが表示されたら、**[Assets]** ディレクトリをクリックして開きます。

3. [Assets] ディレクトリ内で**右クリック**し、**[New]、[Text Document]** の順に選択します。

4. テキスト エディターで新しいテキスト ドキュメントを開き、行 `-r:System.Net.Http.dll` を追加します。

5. ドキュメントを保存して閉じます。

4. 新しいテキスト ドキュメントの名前を "**mcs.rsp**" に変更します。ファイル拡張子の .txt を必ず削除してください。

  * ファイル拡張子が非表示になっている場合、フォルダーの表示オプションを変更し、拡張子を表示する必要があります。
  * [スタート] メニューを開き、「フォルダー オプション」と入力して検索します。 **[エクスプローラーのオプション]** を選択します。
  * **[表示]** タブを選択し、詳細設定で **[登録されている拡張子は表示しない]** のチェックが外されていることを確認します。

    ![エクスプローラーで [Assets] フォルダーを表示する](media/vstu_azure-prepare-dev-environment-image8.png)

以上の手順が完了すると、Unity プロジェクトのルート **[Assets]** ディレクトリの行 `r:System.Net.Http.dll` に **mcs.rsp** という名前のファイルが表示されるはずです。

>[!NOTE]
> 参照機能には Visual Studio Tools for Unity 3.3 以上が必要になります。これは Visual Studio 15.3+ Unity ワークロードに含まれています。 この手順でうまく進まない場合、正しいバージョンの VSTU がインストールされていることを確認してください。

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Newtonsoft.Json NuGet パッケージをプロジェクトに追加する

Azure Mobile Client SDK には Newtonsoft.Json パッケージが必要です。 Unity は NuGet に対応していません。 Visual Studio で Unity プロジェクトを開き、NuGet でパッケージを追加した場合、Unity エディターで次にプロジェクトを開いたとき、パッケージが消去されます。 ただし、NuGet のパッケージを Unity プロジェクトに手動で追加できます。

1. Unity プロジェクトの [Assets] ディレクトリで、"**NuGet Packages**" という名前の新しいフォルダーを作成します。 これはフォルダーを整理する目的で行います。

2. https://www.nuget.org/packages/Newtonsoft.Json/ にアクセスし、**[Manual Download]** ボタンをクリックします。 .nupkg ファイルをダウンロードします。

  ![エクスプローラーで [Assets] フォルダーを表示する](media/vstu_azure-prepare-dev-environment-image9.png)

3. 新しくダウンロードしたファイルを見つけ、ファイル拡張子を .nupkg から **.zip** に変更します。 これで他の zip ファイルと同様に、含まれているファイルを表示し、抽出できるはずです。

4. zip ディレクトリを開くか、抽出し、**\lib\net45** に移動します。

5. **Newtonsoft.Json.dll** ファイルを Unity プロジェクトの **Assets\NuGet Packages** ディレクトリにコピーします。

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Azure Mobile Client SDK NuGet パッケージをプロジェクトに追加する

Azure Mobile Client SDK には、Azure の簡易テーブルで簡単に読み取り/書き込みための機能が含まれています。

1. https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/ にアクセスし、**[Manual Download]** ボタンをクリックします。 .nupkg ファイルをダウンロードします。

2. 新しくダウンロードしたファイルを見つけ、ファイル拡張子を .nupkg から **.zip** に変更します。 これで他の zip ファイルと同様に、含まれているファイルを表示し、抽出できるはずです。

3. zip ディレクトリを開くか、抽出し、**\lib\net45** に移動します。

4. **Microsoft.Azure.Mobile.Client.dll** ファイルを Unity プロジェクトの **Assets\NuGet Packages** ディレクトリにコピーします。

>[!WARNING]
> 以上の手順を完了したら、Unity と Visual Studio を必ず再起動してください。再起動しないと、新しく追加されたパッケージが InteliSense で認識されないことがあります。

## <a name="conclusion"></a>まとめ

以上の手順を完了すると、Azure Mobile Client SDK を使用するように Unity プロジェクトが設定されているはずです。 開発環境をテストできます。その方法として、Unity プロジェクトで新しい C# スクリプトを作成し、それを Visual Studio で開き、一番上に次の using ステートメントを入力します。
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

InteliSense がこのような using ステートメントを検出した場合、設定が正しく完了したことになります。 エラーが表示されたり、InteliSense でこれらのパッケージが認識されない場合、Unity と Visual Studio の再起動をお試しください。 それでもうまくいかない場合、上記の手順をもう一度お試しください。

## <a name="next-step"></a>次のステップ

* [データ モデル クラスを作成する](visual-studio-tools-for-unity-azure-data.md)
