---
title: "クイック スタート: Visual Studio のテンプレートから Python プロジェクトを作成する | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 745e6abe6aa9e1637d7ab79c0f76fb8874e8f6af
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>クイック スタート: Visual Studio のテンプレートから Python プロジェクトを作成する

[Visual Studio 2017 に Python のサポートをインストール](installation.md)すると、さまざまなテンプレートを使用して新しい Python プロジェクトを簡単に作成できます。

1. Visual Studio を起動します。

1. **[ファイル]、[新規]、[プロジェクト]** (Ctrl + Shift + N) の順に選択します。 **[新しいプロジェクト]** ダイアログで、"Python" を検索し、希望のテンプレートを選択します。 テンプレートを選択すると、テンプレートの簡単な説明が表示されます。 (「[Python プロジェクト](python-projects.md#project-templates)」も参照してください。)

    ![VS2017 Python テンプレートの [新しいプロジェクト] ダイアログ](media/projects-new-project-dialog2.png)

1. このクイック スタートでは、"Python アプリケーション" テンプレートを選択し、("MakePI" などの) プロジェクト名を付け、場所を指定し、**[OK]** を選択します。 

1. Visual Studio によってプロジェクト ファイル (ディスク上に 1 つの `.pyproj` ファイル) と、テンプレートに記述されているその他のファイルが作成されます。 "Python アプリケーション" テンプレートでは、プロジェクトと同じ名前の空のファイルのみがプロジェクトに含まれます。 このファイルは、既定で Visual Studio エディタで開きます。

    ![Python アプリケーション テンプレートを使用した結果のプロジェクト](media/projects-new-structure.png)

1. 1000 桁の PI を計算し表示する、次のコードを、開いているファイルに追加します。

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. Ctrl + F5 キーを押すか、メニューを **[デバッグ]、[デバッグなしで開始]** の順に選択して、プログラムを実行します。 結果は、コンソール ウィンドウに表示されます。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [チュートリアル: Visual Studio での Python の使用](vs-tutorial-01-01.md)

## <a name="see-also"></a>関連項目

- [既存の Python インタープリター用の環境の作成](python-environments.md#creating-an-environment-for-an-existing-interpreter)
- [Windows に Visual Studio 2015 の Python サポートをインストールする](installation.md)
- [インストールする場所](installation.md#install-locations)
