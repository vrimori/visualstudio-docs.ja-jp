---
title: Python 検索パスの適用方法
description: Visual Studio で環境とプロジェクトの両方で Python 検索パスが使用されるしくみの概要。
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: d1d05670192630e0bc4903988770c52840a5e347
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118240"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio による Python 検索パスの使用方法

通常の Python の使用方法では、`PYTHONPATH` 環境変数 (または `IRONPYTHONPATH` など) がモジュール ファイルの既定の検索パスを提供します。 つまり、`from <name> import...` または `import <name>` ステートメントを使うと、Python は次の場所を順に検索して、一致する名前を探します。

1. Python の組み込みモジュール
1. 実行している Python コードが含まれるフォルダー
1. 該当する環境変数によって定義された "モジュール検索パス" (Python のコア ドキュメントの「[The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)」(モジュール検索パス) および「[Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH)」(環境変数) をご覧ください)。

ただし、検索パス環境変数がシステム全体に対して設定されている場合でも、Visual Studio はこの変数を無視します。 実際はまさにシステム全体が設定されている*ために*無視されるので、自動的には答えられないようなある種の疑問が発生します。参照されているモジュールは Python 2.7 または Python 3.6 のどちらか。 標準ライブラリ モジュールをオーバーライドするのか。 開発者はこの動作を認識しているのか、それとも悪意のあるハイジャックの試みか。

そのため Visual Studio では、環境とプロジェクトの両方で検索パスを直接指定するための手段が用意されています。 Visual Studio で実行またはデバッグするコードは、検索パスを `PYTHONPATH` (およびその他の同等の変数) の値で受け取ります。 検索パスを追加すると、Visual Studio はそれらの場所でライブラリを検査し、必要に応じて IntelliSense データベースを構築します (Visual Studio 2017 バージョン 15.5 以前、ライブラリの数によっては時間がかかります)。

検索パスを追加するには、ソリューション エクスプローラーで **[Search Paths (検索パス)]** 項目を右クリックし、**[Add Folder to Search Path... (検索パスへのフォルダーの追加...)]** を選んで、含めるフォルダーを選びます。 このパスは、プロジェクトに関連付けられているすべての環境に使われます。 (環境が Python 3 ベースの場合に、検索パスを Python 2.7 モジュールに追加しようとすると、エラーが発生することがあります。)

**[Add Zip Archive to Search Path... (検索パスへの Zip アーカイブの追加...)]** を選ぶことで、拡張子が `.zip` または `.egg` のファイルを検索パスとして追加することもできます。フォルダーと同様に、これらのファイルの内容もスキャンされて、IntelliSense に利用されます。

常に同じ検索パスを使い、内容があまり変化しない場合は、サイトパッケージ フォルダーにインストールする方が効率的な場合があります。 検索パスは分析されて IntelliSense データベースに格納され、常に適切な環境に関連付けられるため、各プロジェクトに検索パスを追加する必要はありません。

## <a name="see-also"></a>関連項目

- [Visual Studio での Python 環境の管理](managing-python-environments-in-visual-studio.md)
- [プロジェクトのインタープリターの選択](selecting-a-python-environment-for-a-project.md)
- [依存関係の requirements.txt の使用](managing-required-packages-with-requirements-txt.md)
- [[Python 環境] ウィンドウ リファレンス](python-environments-window-tab-reference.md)