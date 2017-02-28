---
title: "Visual Studio での Python の概要 | Microsoft Docs"
ms.custom: 
ms.date: 1/3/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d0b0b0b12b9d65f26b67d6f797abc0cf7a0c2c9
ms.openlocfilehash: e7cc978dabb401a8e9bab6791988aa737edb76b0
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-python-in-visual-studio"></a>Visual Studio での Python の概要

Python ([http://python.org/download/](http://python.org/download/)) は、信頼性と柔軟性に優れ、簡単に学ぶことができ、自由に使える一般的なプログラミング言語であり、強力な開発者コミュニティと多くの無料ライブラリによってサポートされています。 Python はすべての主要なオペレーティング システムで機能するため、Web アプリケーション、Web サービス、デスクトップ アプリ、スクリプト、科学技術計算など多くの目的に役立ちます。 そのため、多くの大学、科学者、一般の開発者、およびプロの開発者によって同様に使用されています。

言語に関する詳細については、まず「[Python for Beginners (初心者向けの Python)](https://www.python.org/about/gettingstarted/)」(python.org) を参照してください。

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio

Python Tools for Visual Studio (PTVS) は、Visual Studio 向けの無料で使用できるオープン ソースの拡張機能であり、プロジェクト システムとテンプレート、豊富な編集機能と IntelliSense、フル機能を備えたデバッグ、およびさまざまな他のツールを含む、強力な Python の開発エクスペリエンスを提供します。

拡張機能には、次の機能が用意されています。

- さまざまなバージョンの CPython、IronPython、IPython など、複数のインタープリターのサポート
- Python コードのフォルダー構造を暗黙的に取得し、またアプリ コード、テスト コード、Web ページ、JavaScript、ビルド スクリプトなどを識別できるように、明示的な制御も可能にするプロジェクト システム。
- コンソール、Web、Azure、データ サイエンスおよび他の種類のプロジェクト用のプロジェクト テンプレート。
- 構文の色分け、すべてのコードとライブラリ間でのオートコンプリート、シグネチャ ヘルプ、クラス ビュー、定義への移動、すべての参照の検索、リファクタリングなどを含む、豊富な編集とコード読解の機能。
- 対話型 (REPL) ウィンドウ
- Visual Studio プロジェクトを使用しない機能豊富なデバッグ、既存の実行可能ファイルに対する機能、混合モードのデバッグ、Windows/Linux/Mac へのリモート デバッグ、および対話型ウィンドウ内でのデバッグ。

- データ可視化を備えた IPython。
- IronPython および .NET/WPF のサポート。
- プロファイル ツール。
- テスト用ツール。
- [Azure SDK for Python](#azure-sdk-for-python)

使い始めるにあたり、次のリソースを参考にしてください。

- [Python Tools for Visual Studio をインストールする](https://www.visualstudio.com/vs/python/)。
- [インストール ガイド](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [概要および詳細情報の短いビデオ](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- インストールと機能のデモ (27 分)](https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [ドキュメント](https://github.com/Microsoft/PTVS/wiki)
- [ソース コード](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>Azure SDK for Python

Windows、Mac、および Linux をサポートしている Azure SDK for Python を使用すると、Microsoft Azure サービスの使用と管理が簡単になります。 詳細については、次のリソースを参照してください。

- SDK をインストールするには、「[Python Package Index (Python パッケージ インデックス)](https://pypi.python.org/pypi/azure)」を使用するか、Azure ドキュメントの 「[Python と SDK のインストール](https://azure.microsoft.com/documentation/articles/python-how-to-install/)」の手順に従ってください。
- [Azure SDK for Python デベロッパー センター](http://azure.microsoft.com/en-us/develop/python/)には、チュートリアルによるインストールからドキュメント化までの多数のヘルプがあります。  いくつかの要点を以下に示します。
- 使い方ガイド:
  - [Python から Azure BLOB ストレージを使用する方法](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [Python から Queue ストレージを使用する方法](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [Python から Table ストレージを使用する方法](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [Service Bus キューの使用方法](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [Service Bus のトピックとサブスクリプションの使用方法](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [Python からサービス管理を使用する方法](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- [SDK の GitHub リポジトリ](https://github.com/Azure/azure-sdk-for-python) には、API に関する有益な情報源でもある[単体テスト](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)が含まれています。


## <a name="scientific-computing"></a>科学技術計算
すべての Python データ科学ライブラリに加えて、Python Tools for Visual Studio は、Azure でホスト可能な IPython と IPython Notebooks をサポートしています。

IPython と科学技術計算のライブラリ (matplotlib、scipy、numpy など) を[カリフォルニア大学アーバイン校](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)から入手することをお勧めします。

## <a name="see-also"></a>関連項目
 [PTVS の概要: Visual Studio のセットアップ](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [PTVS の概要: コーディングの開始 (プロジェクト)](../python/getting-started-with-ptvs-start-coding-projects.md)
 [PTVS の概要: コードの編集](../python/getting-started-with-ptvs-editing-code.md)
 [PTVS の概要: デバッグ](../python/getting-started-with-ptvs-debugging.md)
 [PTVS の概要: 対話型の Python](../python/getting-started-with-ptvs-interactive-python.md)
 [PTVS の概要: Azure での Web サイトの作成](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
