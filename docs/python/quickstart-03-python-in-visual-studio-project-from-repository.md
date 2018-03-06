---
title: "クイック スタート - Visual Studio で Python コードのリポジトリを複製する | Microsoft Docs"
description: "Visual Studio チーム エクスプローラーを使って Python Koans リポジトリを複製することにより Python を迅速に使い始めます。"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: a7ddd0f7cf24805eef529d08bf0e37b19fc6a8bc
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>クイック スタート: Visual Studio で Python コードのリポジトリを複製する

[Visual Studio 2017 に Python サポートをインストール](installing-python-support-in-visual-studio.md)すると、Python コードのリポジトリを簡単に複製し、それからプロジェクトを作成できます。

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Visual Studio を起動します。

3. **[ビュー]、[チーム エクスプローラー]** の順に選択し、**[チーム エクスプローラー]** ウィンドウを開きます。ここでは、GitHub または Visual Studio Team Services に接続したり、リポジトリを複製したりできます。

    ![Visual Studio Team Services、GitHub、およびリポジトリの複製が表示された [チーム エクスプローラー] ウィンドウ](media/team-explorer.png)

4. **[Local Git Repositories]\(ローカル Git リポジトリ\)** の下の [URL] フィールドに、`https://github.com/gregmalcolm/python_koans` と入力し、複製されたファイル用のフォルダーを入力し、**[複製]** を選択します。

    > [!Tip]
    > チーム エクスプローラーで指定したフォルダーは、複製されたファイルを受け取る特定のフォルダーです。 `git clone` コマンドとは異なり、チーム エクスプローラーで複製を作成しても、リポジトリの名前のサブフォルダーは自動作成されません。

5. 複製が完了したら、チーム エクスプローラーの下のリポジトリ フォルダーをダブルクリックして、リポジトリのダッシュボードに移動します。 **[ソリューション]** の下で **[新規]** を選択します。

    ![[チーム エクスプローラー] ウィンドウ、複製からの新しいプロジェクトの作成](media/team-explorer-new-project.png)

6. 表示された **[新しいプロジェクト]** ダイアログで、[From Existing Python Code]\(既存の Python コードから)\ を選択し、プロジェクトの名前を指定して、**[場所]** をリポジトリと同じフォルダーに設定し、**[OK]** を選択します。 表示されたウィザードで、**[完了]** をクリックします。

7. メニューから **[表示]、[ソリューション エクスプローラー]** を選択します。

8. ソリューション エクスプローラーで `python3` ノードを展開し、`contemplate_koans.py` を右クリックし、**[スタートアップ ファイルとして設定]** を選択します。 この手順により、プロジェクトの実行時に使用されるファイルが Visual Studio に指示されます。

9. メニューで **[プロジェクト]、[プロパティ]**、**[全般]** タブの順に選択し、**[作業ディレクトリ]** を "python3" に設定します。 これは、既定で Visual Studio がスタートアップ ファイル (`python3\contemplate_koans.py`。これは、プロジェクトのプロパティでも確認できます) の場所ではなく、プロジェクトのルートに作業ディレクトリを設定するために必要です。 プログラム コードは、ファイル `koans.txt` を作業フォルダーから探すので、この値を変更しなくてもランタイム エラーは発生します。

    ![Python プロジェクトの作業ディレクトリの設定](media/projects-set-working-directory.png)

10. Ctrl + F5 キーを押すか、**[デバッグ]、[デバッグなしで開始]** を選択し、プログラムを実行します。 `koans.txt` の `FileNotFoundError` が表示される場合、前の手順の作業ディレクトリの設定を再確認します。

11. プログラムが正常に実行されると、`python3/koans/about_asserts.py` の 17 行にアサーション エラーが表示されます。 これが意図的です。ユーザーが意図的なエラーをすべて修正することにより、プログラムでは、Python にそれが通知されるよう設計されています。 (詳細は、Python Koans にインスピレーションを与えた [Ruby Koans](http://rubykoans.com/) を参照してください。)

    ![Python Koans プログラムからの最初の出力](media/koans-output.png)

12. ソリューション エクスプローラーで `python3/koans/about_asserts.py` に移動し、それを開き、ファイルをダブルクリックします。 エディターには既定で行番号が表示されないことに注意してください。 これを変更するには、**[ツール]、[オプション]** を選択し、ダイアログの下部の **[すべての設定を表示]** を選択し、**[テキスト エディター]、[Python]、[全般]** に移動し、**[行番号]** を選択します。

    ![Python ファイルの行番号の有効化](media/options-general-line-numbers.png)

13. 17 行の `False` 引数を `True` に変更することで、エラーを修正できます。 行を次のようにします。

    ```python
    self.assertTrue(True) # This should be True
    ```

14. プログラムを再実行し、最初のチェックに合格し、プログラムが次の koan で停止することを確認します。 エラーの修正を続け、必要に応じてプログラムを再実行します。

> [!Important]
> このクイック スタートでは、GitHub の *python_koans* リポジトリの複製を直接作成しました。 このようなリポジトリは、直接変更できないように作成者によって保護されているため、そのリポジトリに変更をコミットしようとすると失敗します。 実際には、代わりに開発者が自分の GitHub アカウントにこのようなリポジトリをフォークし、プル要求を作成し、元のリポジトリにそれらの変更を送信します。 これらの手順は、「[Tutorial Step 6 - Working with Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)」(チュートリアル手順 6: Git の使用) で説明しています。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [チュートリアル: Visual Studio での Python の使用](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>関連項目

- [既存の Python インタープリターを手動で識別する](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)
- [Windows に Visual Studio 2015 の Python サポートをインストールする](installing-python-support-in-visual-studio.md)
- [インストールする場所](installing-python-support-in-visual-studio.md#install-locations)
