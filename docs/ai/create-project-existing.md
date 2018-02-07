# <a name="create-an-ai-project-from-existing-code"></a>既存のコードから AI プロジェクトを作成する

[Visual Studio Tools for AI をインストール](installation.md)したら、Visual Studio プロジェクトに既存の Python コードを簡単に取り込むことができます。

> [!Important]
>
> ここで説明するプロセスでは、元のソース ファイルの移動やコピーは行いません。 コピーで作業する場合は、まず、フォルダーを複製します。

1. Visual Studio を起動し、**[ファイル]、[新規作成]、[プロジェクト]** の順に選びます。

1. **[新しいプロジェクト]** ダイアログで、"**AI Tools**" を検索し、**[既存の Python コードから]** テンプレートを選択し、プロジェクトの名前と場所を指定し、**[OK]** を選びます。

    ![[既存のコードから新しいプロジェクトを作成]、手順 1](media\create-project-existing\new-ai-project.png)

1. 表示されるウィザードで、既存のコードへのパスを設定し、ファイルの種類に関するフィルターを設定し、プロジェクトで必要な検索パスを指定して、**[OK]** を選びます。 検索パスが不明である場合は、そのフィールドを空白のままにします。

![[既存のコードから新しいプロジェクトを作成]、手順 2](media\create-project-existing\azurebatch-newproject.png)

> 既存のコードが Azure Machine Learning プロジェクトの一部である場合は、**[Is Azure Machine Learning folder]\(Azure Machine Learning フォルダーである\)** をオンにして、Azure Machine Learning の重要な構成の詳細 (使用する実験アカウント、ワークスペース、計算コンテキストなど) が正常に変換されるようにします。

1. スタートアップ ファイルを設定するには、ソリューション エクスプローラーでファイルを特定し、右クリックして、**[スタートアップ ファイルとして設定]** を選びます。

1. 必要に応じて、Ctrl + F5 キーを押すか、**[デバッグ]、[デバッグなしで開始]** の順に選択して、プログラムを実行します。

> [!div class="nextstepaction"]
> [チュートリアル: Visual Studio での Python の使用](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>参照

- [既存の Python インタープリター用の環境の作成](../python/managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter)