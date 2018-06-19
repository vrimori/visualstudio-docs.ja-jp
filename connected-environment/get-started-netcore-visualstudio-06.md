---
title: クラウドで Kubernetes と Visual Studio を使用して、コンテナーを含む .NET Core 開発環境を作成する - 手順 6 - チーム開発について学習する | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Azure でのコンテナーおよびマイクロサービスを使用する迅速な Kubernetes 開発
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: douge
ms.openlocfilehash: b4bc1f44e63614346f4e2d149e76becabdcb8c71
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899415"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Connected Environment で .NET Core と Visual Studio の使用を開始する

前の手順: [別のコンテナーを呼び出す](get-started-netcore-visualstudio-05.md)

## <a name="learn-about-team-development"></a>チーム開発について学習する

ここまでは、アプリケーションを扱う唯一の開発者であるかのようにアプリケーションのコードを実行しました。 このセクションでは、Connected Environment がチーム開発をどのように効率化するかについて説明します。
* 開発者チームが同じ開発環境で作業できるようにします。
* 各開発者が他の開発者の邪魔してしまうことを心配せずに、隔離された状態でコードを反復処理できるようにします。
* 依存関係のシミュレーションやモックの作成を行わずに、コードのコミットの前に、コードをエンド ツー エンドでテストします。

## <a name="challenges-with-developing-microservices"></a>マイクロサービスの開発に伴う課題
現時点では、このサンプル アプリケーションはそれほど複雑ではありません。 しかしながら、実際の開発では、サービスがさらに追加され開発チームが拡大すると、すぐに課題が生じます。

他の多くのサービスと対話するサービスで作業するご自分の姿を想像してみてください。

1. 開発のためにすべてをローカルで実行するのは非現実的になる可能性があります。 開発用コンピューターには、アプリ全体を実行するのに十分なリソースがないこともあります。 また、ご利用のアプリに、パブリックに到達可能である必要があるエンドポイントがある場合もあります (アプリで SaaS アプリからの webhook に応答するなど)。
1. 依存するサービスのみの実行を試みることはできますが、その場合、依存関係の完全なクロージャー (依存関係の依存関係など) を確認する必要があります。 あるいは、依存関係を扱っていなかったため、依存関係を構築し、実行する方法が簡単にはわからないという問題です。
1. 開発者には、サービスの依存関係の多くをシミュレートしたり、モックを作成したりする方法をとる者もいます。 この方法でうまくいくこともありますが、開発時にすぐにモックの管理に苦労することになる可能性があります。 また、開発環境と運用環境が非常に異なって見えるようになり、バグが知らない間に入り込む可能性もあります。
1. その結果、あらゆる種類のエンドツーエンド テストが困難になります。 実際には、統合テストはコミット後にのみ行われます。つまり、問題は開発サイクルの後半に発生します。

    ![](media/microservices-challenges.png)

## <a name="work-in-a-shared-development-environment"></a>共有開発環境で作業する
Connected Environment を使用すれば、Azure で*共有* 開発環境を設定することができます。 各開発者はアプリケーションの自分の担当部分にのみに集中できます。自分のシナリオが依存する他のすべてのサービスとクラウド リソースが既に含まれている環境で*事前コミット コード*を繰り返し開発できます。 依存関係は常に最新の状態になります。開発者は運用環境を反映した方法で作業します。

## <a name="work-in-your-own-space"></a>自分のスペースで作業する
サービスのコードを開発するときに、まだチェックインの段階でなければ、多くの場合、コードは良好な状態ではありません。 それでも、繰り返し調整し、テストし、ソリューションを試します。 Connected Environment では、**スペース**という概念を導入しています。このスペースにより、チーム メンバーの邪魔をすることを心配せずに、隔離された状態で作業できます。

次の操作を行って、`webfrontend` および `mywebapi` サービスの両方が開発環境**と `mainline` スペース**で実行されていることを確認します。
1. 両方のサービスの F5/デバッグ セッションをすべて閉じます。ただし、Visual Studio ウィンドウではプロジェクトを開いたままにします。
2. `mywebapi` プロジェクトがある Visual Studio ウィンドウに切り替え、Ctrl + F5 キーを押してデバッガーをアタッチせずにサービスを実行します。
3. `webfrontend` プロジェクトがある Visual Studio ウィンドウに切り替え、Ctrl + F5 キーを押して同様に実行します。

> [!Note]
Ctrl + F5 キーを押して最初に Web ページが表示された後に、ブラウザーを更新する必要がある場合があります。

パブリック URL を開き、Web アプリに移動するすべてのユーザーは、作成済みのコード パスを呼び出します。これは、既定の `mainline` スペースを使用して、両方のサービスで実行されます。 `mywebapi` の開発を続行するとします。開発環境を使用している他の開発者を邪魔せずに続行するにはどうすればよいでしょうか。 それには、自分だけのスペースを設定します。

### <a name="create-a-new-space"></a>新しいスペースを作成する
Visual Studio 内から、ご利用のサービスについて F5 キーまたは Ctrl + F5 キーを押すときに使用される追加スペースを作成することができます。 スペースにはどのような名前を付けてもかまいません。内容に合わせて自由に名前を付けることができます (例:  `sprint4` または `demo`)。

新しいスペースを作成するには、次の操作を行います。
1. `mywebapi` プロジェクトがある Visual Studio ウィンドウに切り替えます。
2. **ソリューション エクスプローラー**でプロジェクトを右クリックして、**[プロパティ]** を選択します。
3. 左側の **[デバッグ]** タグを選択して、Connected Environment の設定を表示します。
4. ここから、F5 キーまたは Ctrl + F5 を押すときに使用されるスペースや Connected Environment を変更または作成することができます。 *以前に作成した Connected Environment が選択されていることを確認します*。
5. **[スペース]** ドロップダウンで、**[<Create New Space…>]\(<新しいスペースの作成…>\)** を選択します。

    ![](images/Settings.png)

6. **[スペースの追加]** ダイアログで、スペースの名前を入力して **[OK]** をクリックします。 誰が作業しているスペースであるかを同僚が識別できるように、新しいスペースには自分の名前 ("scott") を使用しました。

    ![](images/AddSpace.png)

7. これで、プロジェクト プロパティ ページで選択した新しいスペースと開発環境が表示されます。

    ![](images/Settings2.png)

### <a name="update-code-for-mywebapi"></a>*mywebapi* のコードを更新する

1. `mywebapi` プロジェクトで、次のように `ValuesController.cs` ファイルで `string Get(int id)` メソッドのコードを変更します。
 
    ```csharp
    [HttpGet("{id}")]
    public string Get(int id)
    {
        return "mywebapi now says something new";
    }
    ```

2. この更新されたコード ブロックでブレークポイントを設定します (既に 1 つ設定されている可能性があります)。
3. F5 キーを押して、`mywebapi` サービスを開始します。 これにより、選択されたスペース (ここでは `scott`) を使用して開発環境でサービスが開始されます。

さまざまなスペースのしくみを理解するのに役立つ図を以下に示します。 青色のパスは `mainline` スペースによる要求を示しています。この既定のパスは、URL にスペースが付加されない場合に使用されます。 緑色のパスは、`scott` スペースによる要求を示しています。

![](media/Space-Routing.png)

Connected Environment のこの組み込み機能を使用すれば、共有環境でコードをエンド ツー エンドでテストできます。各開発者が自分のスペースでサービスの完全なスタックを再作成する必要はありません。 このガイドの前の手順で示したように、このルーティングでは伝達ヘッダーをアプリ コードで転送する必要があることに注意してください。

## <a name="test-code-running-in-the-scott-space"></a>`scott` スペースで実行されているコードをテストする
新しいバージョンの `mywebapi` を `webfrontend` と共にテストするには、ブラウザーで `webfrontend` のパブリック アクセス ポイントの URL (例:  https://webfrontend-teamenv.vsce.io) を開き、About ページに移動します。 "Hello from webfrontend and Hello from mywebapi" という元のメッセージが表示されます。

ここで、https://scott-webfrontend-teamenv.vsce.io のようになるように URL に "scott-" の部分を追加して、ブラウザーを更新します。 `mywebapi` プロジェクトで設定したブレークポイントにヒットします。 F5 キーを押して続行します。これで、ブラウザーに新しいメッセージの "Hello from webfrontend and mywebapi now says something new" が表示されます。 これは、`mywebapi` で更新したコードへのパスが `scott` スペースで実行されているためです。

> [!div class="nextstepaction"]
> [まとめ](get-started-netcore-visualstudio-07.md)