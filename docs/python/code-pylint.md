---
title: "Visual Studio での PyLint の使用 | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 4b22d434b99bdd2648408b9191c5f050589883ae
ms.contentlocale: ja-jp
ms.lasthandoff: 08/14/2017

---

# <a name="using-pylint-to-check-python-code"></a>PyLint を使用した Python コードのチェック

Visual Studio for Python プロジェクトには [PyLint](https://www.pylint.org/) が組み込まれています。これは広く用いられている Python コードのエラー チェックツールで、優れた Python のコード パターンを作成するのに役立ちます。

使用するには、ソリューション エクスプローラーで Python プロジェクトを右クリックし、**[Python] > [Run PyLint (PyLint の実行)]** を選択するだけです。

![Python プロジェクトのコンテキスト メニューに表示された PyLint コマンド](media/code-pylint-command.png)

このコマンドを使用すると、PyLint が存在しない場合は、アクティブな環境内に PyLint をインストールするように求められます。

PyLint の警告とエラーが [エラー一覧] ウィンドウに表示されます。

![PyLint のエラー一覧](media/code-pylint-error-list.png)

エラーをダブルクリックすると、問題が発生したソース コードに直接移動できます。

> [!Tip]
> PyLint のすべての出力メッセージの詳細な一覧については、[PyLint の機能のリファレンス](https://pylint.readthedocs.io/en/latest/technical_reference/features.html)に関するページをご覧ください。

## <a name="setting-pylint-command-line-options"></a>PyLint コマンド ライン オプションの設定

PyLint ドキュメントの[コマンド ライン オプション](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)のセクションでは、`.pylintrc` 構成ファイルを使用して PyLint の動作を制御する方法が説明されています。 このようなファイルは Visual Studio 内の Python プロジェクトのルートに配置するか、設定を適用したい範囲に応じて他の場所に配置します。

たとえば、前の画像に表示されている "docstring が見つかりません" という警告がプロジェクト内の `.pylintrc` ファイルに対して表示されないようにするには、次の手順を実行します。

1. コマンド ラインで、プロジェクトのルート (`.pyproj` ファイルが含まれる) に移動し、次のコマンドを実行してコメント付きの構成ファイルを生成します。

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. Visual Studio のソリューション エクスプローラーでプロジェクトを右クリックし、**[追加] > [既存の項目]** を選択します。新しい `.pylintrc` ファイルを見つけて選択し、**[追加]** を選択します。

1. ファイルを編集のために開くと、操作できる各種の設定が表示されます。 警告を無効にするには、`[MESSAGES CONTROL]` セクションを探し、そのセクションの `disable` 設定を見つけます。 特定のメッセージからなる長い文字列が表示されます。ここに目的の警告を追加できます。 この例では、`,missing-docstring` (区切りコンマを含む) を追加します。

1. `.pylintrc` ファイルを保存し、PyLint をもう一度実行して、警告が表示されなくなったことを確認します。

