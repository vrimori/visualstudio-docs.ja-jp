---
title: クラウドで Kubernetes と Visual Studio を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 3 - Kubernetes 開発環境を作成する | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: 6226340b1744e95bbb375d47213ae00bb9e76565
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884386"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Connected Environment で .NET Core と Visual Studio の使用を開始する

前の手順: [ASP.NET Web アプリを作成する](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>Azure で開発環境を作成する
Connected Environment を使用すれば、Azure で完全に管理され、開発用に最適化された、Kubernetes ベースの開発環境を作成することができます。 作成したプロジェクトを開いた状態で、次のように起動設定ドロップダウンから **[Connected Environment for AKS]** を選択します。

![](images/LaunchSettings.png)

次に表示されるダイアログで、適切なアカウントでサインインしていることを確認し、既存の開発環境を選択するか、**[<Create New Connected Environment for AKS…>]\(新しい Connected Environment for AKS の作成...\)** を選択して新しい環境を作成します。

![](images/ConnectedEnvDialog.png)

指定された既定値を使用することも、好きなように調整することもできます。 値が適切に設定されたら、**[OK]** をクリックします。

![](images/NewEnvDialog.png)

前のダイアログに戻り、現時点では **[スペース]** ドロップダウンは既定の `mainline` のままにしておきます。これについては、後で詳しく説明します。 **[Publicly Accessible]\(パブリックにアクセス可能\)** チェック ボックスをオンにして、Web アプリにパブリック エンドポイント経由でアクセスできるようにします。 これは必須ではありませんが、このチュートリアルの後半でいくつかの概念を示すために役立ちます。 いずれにせよ、Visual Studio を使用して Web サイトをデバッグできるので心配はありません。

![](images/ConnectedEnvDialog2.png)

**[OK]** をクリックして、開発環境を選択するか作成します。 これを実行するためにバックグラウンド タスクが開始され、完了するまで数分かかります。 ステータス バーの左下隅にある**バックグラウンド タスク** アイコンにカーソルを置くことで、まだ作成中であるかどうかを確認できます (下記参照)。

![](images/BackgroundTasks.png)

> [!Note]
開発環境が正常に作成されるまでは、アプリケーションをデバッグすることはできません。

## <a name="look-at-the-files-added-to-project"></a>プロジェクトに追加されたファイルを見る
開発環境が作成されるのを待っている間に、開発環境の使用を選択したときにプロジェクトに追加されたファイルを見てみましょう。

最初に、`charts` という名前のフォルダーが追加されており、この中にアプリケーション用の [Helm チャート](https://docs.helm.sh)がスキャフォールディングされていることを確認します。 これらのファイルは、開発環境にアプリケーションを展開するために使用されます。

`Dockerfile` という名前のファイルが追加されていることを確認します。 このファイルには、標準の Docker 形式でアプリケーションをパッケージ化するために必要な情報が含まれています。 `HeaderPropagation.cs` ファイルも作成されます。このファイルについては、チュートリアルの後半で説明します。 

最後に、アプリケーションがパブリック エンドポイント経由でアクセス可能であるかどうかなど、開発環境で必要な構成情報を含む、`vsce.yaml` という名前のファイルを確認します。

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [Kubernetes でコンテナーをデバッグする](get-started-netcore-visualstudio-04.md)