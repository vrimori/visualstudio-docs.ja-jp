---
title: "Visual Studio での C++ と Python の使用 | Microsoft Docs"
ms.custom: 
ms.date: 09/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
description: "Visual Studio で Python 用に C++ の拡張機能またはモジュールを記述するプロセスと手順について説明します"
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 08f91846340e2acc993e5302badfc846db5f4a9c
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="creating-a-c-extension-for-python"></a>Python 用 C++ 拡張機能の作成

Python インタープリターの機能を拡張するため、およびオペレーティング システムの低レベル機能にアクセスするためには、C++ (または C) で記述されたモジュールがよく使われます。 モジュールの主要な種類は次の 3 つです。

- アクセラレータ モジュール: Python はインタープリター言語であるため、コードの特定の部分を C++ で書くことによってパフォーマンスを向上させることができます。 
- ラッパー モジュール: ラッパーは、既存の C/C++ インターフェイスを Python コードに公開します。また、Python から使いやすい、より "Python らしい" API を公開します。
- 低レベル システム アクセス モジュール: CPython ランタイム、オペレーティング システム、または基盤ハードウェアの低レベル機能にアクセスするために作成します。 

このトピックでは、双曲正接を計算する CPython 用の C++ 拡張モジュールを作成し、Python コードからそれを呼び出す手順について説明します。 Python では最初にルーチンを実装して、C++ で同じルーチンを実装した場合のパフォーマンス向上を示します。

ここでは、[Python のドキュメント](https://docs.python.org/3/c-api/)で説明されている CPython の標準拡張機能のためのアプローチを使います。 この方法と他の方法の比較については、このトピックの最後にある「[別の方法](#alternative-approaches)」で説明します。

## <a name="prerequisites"></a>必須コンポーネント

- **C++ によるデスクトップ開発**と **Python 開発**ワークロードの両方を備えた Visual Studio 2017 が既定のオプションでインストールされます。 
- **Python 開発**ワークロードでは、**[Python ネイティブ開発ツール]** のチェック ボックスもオンにし、それによりこのトピックで説明するほとんどのオプションが設定されます (このオプションには、C++ のワークロードも自動的に含まれます)。 

![[Python ネイティブ開発ツール] オプションの選択](media/cpp-install-native.png)

- **データ サイエンスと分析アプリケーション** ワークロードをインストールすることでも、Python と **Python ネイティブ開発ツール** オプションが既定で含まれます。

他のバージョンの Visual Studio の使用など、詳細については「[Visual Studio 用の Python サポートのインストール](installation.md)」を参照してください。 Python を別にインストールする場合は、インストーラーで **[詳細オプション]** の **[Download debugging symbols (デバッグ シンボルのダウンロード)]** と **[Download debug binaries (デバッグ バイナリのダウンロード)]** を必ず選んでください。 このオプションを選択すると、デバッグ ビルドを行う場合に、必要なデバッグ ライブラリを確実に使用できます。

## <a name="create-the-python-application"></a>Python アプリケーションを作成する

1. Visual Studio で **[ファイル]、[新規]、[プロジェクト]** の順に選択して、新しい Python プロジェクトを作成します。 "Python" を検索し、**Python アプリケーション** テンプレートを選択し、適切な名前と場所を指定し、**[OK]** を選択します。

1. プロジェクトの `.py` ファイルに、双曲正接の計算をベンチマークする次のコードを貼り付けます (簡単に比較できるよう、数値演算ライブラリを使わずに実装されています)。 自由に手動でコードを入力し、[Python の編集機能](code-editing.md)を体験してください。

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. **[デバッグ] > [デバッグなしで開始]** (Ctrl + F5 キー) を使ってプログラムを実行し、結果を確認します。 `COUNT` 変数を調整して、ベンチマークの実行にかかる時間を変更することができます。 このチュートリアルの目的は、各ベンチマークの所要時間を約 2 秒にするように、カウントを設定することです。

## <a name="create-the-core-c-project"></a>C++ のコア プロジェクトを作成する

1. ソリューション エクスプローラーでソリューション名を右クリックし、**[追加] > [新しいプロジェクト...]** を選びます。同じ Visual Studio ソリューションに、Python と C++ 両方のプロジェクトを含めることができます。

1. "C++" を検索し、**[空のプロジェクト]** を選び、名前 (TanhBenchmark など) を指定して、**[OK]** を選びます。 注: Visual Studio 2017 で **Python ネイティブ開発ツール**をインストールした場合は、**Python 拡張モジュール**から始めることができます。このテンプレートには、ここで説明するものの多くが既に配置されています。 ただし、このチュートリアルでは、拡張モジュールの作成手順を実際に示すため、空のプロジェクトから始めます。

1. **[ソース ファイル]** ノードを右クリックし、**[追加] > [新しい項目...]** を選び、**[C++ ファイル]** を選んで名前 (`module.cpp` など) を指定してから **[OK]** を選び、新しいプロジェクトに C++ ファイルを作成します。 このステップは、次のステップで C++ のプロパティ ページを有効にするために必要です。

1. 新しいプロジェクトを右クリックして **[プロパティ]** を選び、表示される **[プロパティ ページ]** ダイアログ ボックスの上部で、**[構成]** を **[すべての構成]** に設定します。

1. 以下に示すように、特定のプロパティを設定し、**[OK]** を選択します。

    | タブ | プロパティ | 値 | 
    | --- | --- | --- |
    | 全般 | [全般] > [ターゲット名] | Python が認識するモジュールの名前と完全に一致するようにこのフィールドを設定します。 |
    | | [全般] > [ターゲットの拡張子] | .pyd |
    | | [プロジェクトの既定値] > [構成の種類] | ダイナミック ライブラリ (.dll) |
    | [C/C++] > [全般] | 追加のインクルード ディレクトリ | インストールに合わせて Python の `include` フォルダーを追加します (例: `c:\Python36\include`) |     
    | [C/C++] > [プリプロセッサ] | プリプロセッサの定義 | 文字列の先頭に `Py_LIMITED_API;` を追加し、Python から呼び出すことができる一部の関数を制限し、Python の異なるバージョン間でのコードの移植性を高くします。 |
    | [C/C++] > [コード生成] | ランタイム ライブラリ | マルチスレッド DLL (/MD) (下記の「警告」を参照) |
    | [リンカー] > [全般] | 追加のライブラリ ディレクトリ | インストールに合わせて、`.lib` ファイルが含まれる Python の `libs` フォルダーを追加します (例: `c:\Python36\libs`) (`.py` ファイルが含まれる `Lib` フォルダーでは*なく*、`.lib` ファイルが含まれる `libs` フォルダーを必ず指定してください)。 | 

    > [!Tip]
    > [C/C++] タブが表示されない場合は、C/C++ ソース ファイルとして識別されるファイルがプロジェクトに含まれないためです。 このような条件は、`.c` または `.cpp` 拡張子を付けずにソース ファイルを作成すると発生する可能性があります。 たとえば、前の [新しい項目] ダイアログで、つい `module.cpp` ではなく `module.coo` と入力してしまった場合、Visual Studio はファイルを作成しますが、ファイルの種類を "C/C++ コード" に設定しないので、C/C++ のプロパティ タブがアクティブになりません。この識別の誤処理は、ファイル名を `.cpp` に変更しても解決しません。 ファイルの種類を正しく設定するには、ソリューション エクスプローラーでファイルを右クリックして **[プロパティ]** を選び、**[ファイルの種類]** を **[C/C++ コード]** に設定します。

    > [!Warning]
    > デバッグ構成であっても、**[C/C++] > [コード生成] > [ランタイム ライブラリ]** オプションを [マルチスレッド デバッグ DLL (/MDd)] に設定しないでください。 非デバッグ Python バイナリのビルドに使われている [マルチスレッド DLL (/MD)] ランタイムを選択してください。 /MDd オプションを設定すると、DLL のデバッグ構成をビルドするときに、*C1189: Py_LIMITED_API は Py_DEBUG、Py_TRACE_REFS、Py_REF_DEBUG と互換性がありません*というエラーが表示されます。 さらに、ビルド エラーを避けるために `Py_LIMITED_API` を削除すると、モジュールをインポートしようとしたときに Python がクラッシュします (後で説明しますが、クラッシュは DLL の`PyModule_Create` の呼び出し内で発生し、出力メッセージは "*Fatal Python error: PyThreadState_Get: no current thread (Python 致命的エラー: PyThreadState_Get: 現在のスレッドがありません)*" です)。
    >
    > /MDd オプションは Python デバッグ バイナリ (python_d.exe など) のビルドに使われますが、拡張 DLL に対して選ぶと、やはり `Py_LIMITED_API` のビルド エラーになることに注意してください。
   
1. C++ プロジェクトを右クリックし、**[ビルド]** を選んで構成をテストします (デバッグとリリースの両方)。 `.pyd` ファイルは、C++ のプロジェクト フォルダー自体ではなく、**Debug** および **Release** の下の *solution* フォルダーにあります。

1. C++ プロジェクトのメインの `.cpp` ファイルに、次のコードを追加します。

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. C++ プロジェクトを再度ビルドし、コードが正しいことを確認します。


## <a name="convert-the-c-project-to-an-extension-for-python"></a>C++ プロジェクトを Python の拡張機能に変換する

C++ DLL を Python の拡張機能にするには、Python の型と対話するようにエクスポートしたメソッドを変更する必要があります。 その後、モジュールのメソッドの定義と共に、モジュールをエクスポートする関数を追加する必要があります。 これらの背景については、python.org で「[Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html)」(Python/C API リファレンス マニュアル) および特に「[Module Objects](https://docs.python.org/3/c-api/module.html)」(モジュールのオブジェクト) をご覧ください(右上のドロップダウン コントロールで Python のバージョンを選んでください)。

1. C++ ファイルの先頭に `Python.h` を含めます。

    ```cpp
    #include <Python.h>
    ```

1. Python の型を受け付けて戻すように、`tanh_impl` メソッドを変更します。

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Python に対して C++ の `tanh` 関数を提示する方法を定義する構造体を追加します。

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Python コードで認識されるモジュールを定義する構造体を追加します  (module.cpp などの、C++ プロジェクト内部のファイル名は重要ではありません)。

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name as Python sees it
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. モジュールを読み込むときに Python が呼び出すメソッドを追加します。`PyInit_<module-name>` という名前にする必要があります。*&lt;module_name&gt;* は、C++ プロジェクトの **[全般] > [ターゲット名]** プロパティと正確に一致します (つまり、プロジェクトによってビルドされる `.pyd` のファイル名と一致します)。

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. もう一度 C++ プロジェクトをビルドして、コードを検証します。

## <a name="test-the-code-and-compare-the-results"></a>コードをテストして結果を比較する

Python 拡張機能の構造の DLL ができたので、Python プロジェクトからそれを参照し、モジュールをインポートして、そのメソッドを使うことができます。

### <a name="make-the-dll-available-to-python"></a>Python で DLL を使用できるようする

Python で DLL を使えるようにするには 2 つの方法があります。

第 1 の方法は、Python プロジェクトと C++ プロジェクトが同じ Visual Studio ソリューション内にある場合に有効で、Python プロジェクトから C++ プロジェクトへの参照を追加します。

1. ソリューション エクスプローラーで、Python プロジェクト内の **[参照設定]** ノードを右クリックし、**[参照の追加]** をクリックします。 表示されるダイアログの **[プロジェクト]** タブで、**superfastcode** プロジェクト (または使用している名前) を選択し、**[OK]** を選択します。

第 2 の方法は、グローバル Python 環境にモジュールをインストールし、他の Python プロジェクトでも使えるようにします。 そのためには、通常、その環境に合わせて IntelliSense 入力候補データベースを更新する必要があります。 環境からモジュールを削除するときも、更新する必要があります。

1. Visual Studio 2017 を使っている場合は、Visual Studio インストーラーを実行して **[変更]** を選び、**[個別のコンポーネント] > [コンパイラ、ビルド ツール、およびランタイム] > [Visual C++ 2015.3 v140 ツールセット]** を選びます。 この手順が必要な理由は、Python (for Windows) 自体が Visual Studio 2015 (バージョン 14.0) でビルドされ、ここで説明する方法で拡張機能をビルドするときはこれらのツールが使えることが想定されるためです。

1. プロジェクトを右クリックし、**[追加] > [新しい項目]** を選択して、C++ プロジェクトに `setup.py` という名前のファイルを作成します。次に、"C++ File (.cpp)" を選択し、ファイルに `setup.py` という名前を付け、**[OK]** を選択します (`.py` 拡張子を使用してファイルに名前を付けることで、C++ ファイル テンプレートを使用していても、Visual Studio でそのファイルが Python として認識されるようにします)。 ファイルがエディターに表示されたら、そこに次のコードを貼り付けます。

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    このスクリプトについては、「[Building C and C++ Extensions](https://docs.python.org/3/extending/building.html)」(C と C++ の拡張機能のビルド) (python.org) をご覧ください。

1. `setup.py` コードをコマンド ラインから使用すると、Visual Studio 2015 C++ ツールセット使って拡張機能をビルドするように Python に指示します。 管理者特権でコマンド プロンプトを開き、C++ プロジェクト (および `setup.py`) を含むフォルダーに移動して、次のコマンドを入力します。

    ```
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Python から DLL を呼び出す

上記のいずれかの方法が完了したら、`fast_tanh` 関数を呼び出し、そのパフォーマンスを Python の実装と比較できるようになります。

1. 次の行を `.py` ファイルに追加して、DLL からエクスポートされた `fast_tanh` メソッドを呼び出してその出力を表示します。 `from s` ステートメントを手入力する場合は、入力候補一覧に `superfastcode` が表示され、「`import`」と入力すると `fast_tanh` メソッドが表示されます。

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Python プログラムを実行すると、Python の実装より C++ ルーチンの方が 5 から 20 倍速いことがわかります。 違いがより顕著になるように、もう一度、`COUNT` 変数を増やしてみます。 また、C++ モジュールのリリース ビルドの実行は、デバッグ ビルドよりも高速になることに注意してください。これは、デバッグ ビルドが十分に最適化されず、さまざまなエラー チェックが含まれるためです。 これらの構成間を自由に切り替えて比較することができます。

## <a name="debug-the-c-code"></a>C++ コードをデバッグする

Visual Studio では、Python と C++ コードを一緒にデバッグすることをサポートしています。

1. ソリューション エクスプローラーで Python プロジェクトを右クリックして、**[プロパティ]** の **[デバッグ]** タブを選び、**[デバッグ] > [ネイティブ コードのデバッグを有効にする]** オプションをオンにします。

    > [!Tip]
    > ネイティブ コードのデバッグを有効にすると、プログラムが通常の [続行するには、任意のキーを押してください] で一時停止せずに完了した場合に、Python の出力ウィンドウがすぐに消えることがあります。 強制的に一時停止するには、ネイティブ コードのデバッグを有効にするときに、**[デバッグ]** タブの **[実行] > [インタープリターの引数]** フィールドに、`-i` オプションを追加します。 この引数を使用すると、Python インタープリターはコード終了後に対話モードになり、この時点でユーザーが Ctrl + Z キー、Enter キーの順に押して終了するのを待機します。 (または、Python コードを変更してもよい場合は、プログラムの最後に `import os` および `os.system("pause")` ステートメントを追加します。 このコードで、元の一時停止プロンプトが複製されます)。

1. **[ファイル] > [保存]** を選択して、プロパティの変更を保存します。

1. Visual Studio ツールバーで、ビルド構成を [デバッグ] に設定します。 

    ![ビルド構成を [デバッグ] に設定する](media/cpp-set-debug.png)

1. 通常デバッガーでコードを実行するとより時間がかかるため、`.py` ファイルの `COUNT` 変数を約 5 倍小さい値 (たとえば、`500000` から `100000`) に変更できます。

1. C++ コードで `tanh_impl` メソッドの先頭行にブレークポイントを設定して、(F5 を押すか、**[デバッグ] > [デバッグの開始]** の順に選択して) デバッガーを開始します。 そのコードが呼び出されるとデバッガーが停止します。 ブレークポイントがヒットしない場合は、構成が [デバッグ] に設定されていること、およびプロジェクトを保存していること (これはデバッガーの開始時に自動的に行われません) を確認します。

    ![C++ コードのブレークポイントでの停止](media/cpp-debugging.png)

1. この時点で、C++ コードをステップ実行したり、変数を調べたりできます。 これらの機能の詳細については、「[Python と C++ の同時デバッグ](debugging-mixed-mode.md)」をご覧ください。

## <a name="alternative-approaches"></a>別の方法 

次の表で説明するように、Python の拡張機能を作成するにはさまざまな方法があります。 CPython の最初のエントリは、このトピックで既に説明したものです。

| 方法 | 時期 | 代表的ユーザー | 長所 | 短所 |
| --- | --- | --- | --- | --- |
| CPython 用の C/C++ 拡張モジュール | 1991 | 標準ライブラリ | [広範なドキュメントとチュートリアル](https://docs.python.org/3/c-api/)。 総合的な制御。 | コンパイル、移植性、参照の管理。 C についての深い知識。 |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 多くの言語のバインドを一度に生成。 | Python が唯一のターゲットである場合、過剰なオーバーヘッド。 |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | コンパイルがなく、広く利用可能。 | C 構造体のアクセスや変更が煩雑で、エラーを起こしやすい。 |
| Cython | 2007 | [gevent](http://www.gevent.org/)、[kivy](https://kivy.org/) | Python に似ている。 非常に完成されている。 高パフォーマンス。 | コンパイル、新しい構文、ツールチェーン。 |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/)、[pypy](http://pypy.org/) | 容易な統合、PyPy との互換性。 | 新しく、未完成な部分がある。 |
