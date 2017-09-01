---
title: "Visual Studio での Python コードの書式設定 | Microsoft Docs"
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
ms.assetid: 3d0f1631-360b-45d4-a0cb-01c3c10d25f2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 9d04c52a595014d06b38205913e3eb1cdd264019
ms.contentlocale: ja-jp
ms.lasthandoff: 07/18/2017

---

# <a name="formatting-python-code"></a>Python コードの書式設定

Visual Studio を使用すると、事前に構成した書式設定オプションに合わせて、コードの書式をすばやく設定できます。

- 選択範囲の書式を設定するには、**[編集] > [詳細設定] > [選択範囲のフォーマット]** を選択するか、Ctrl + E、F キーを押します。
- ファイル全体の書式を設定するには、**[編集] > [詳細設定] > [ドキュメントのフォーマット]** を選択するか、Ctrl + E、D キーを押します。

オプションは **[ツール] > [オプション] > [テキスト エディター] > [Python] > [書式設定]** とその入れ子になったタブで設定しますが、既定値は [PEP 8 スタイル ガイド](http://www.python.org/dev/peps/pep-0008/)のスーパーセットに従って設定されます。 **[全般]** タブでは、どのような場合に書式設定を適用するかを指定します。このトピックでは、他の 3 つのタブについて説明します。

[Visual Studio の Python のサポート](installation.md)で、**[編集] > [詳細設定]** には、[[コメントを段落幅に合わせる]](#fill-comment-paragraph-command) という便利なコマンドも追加されています。これについても後で説明します。

## <a name="spacing"></a>スペース

**[スペース]** では、さまざまな言語コンストラクトの前後のスペースを挿入するか削除するかを指定します。 各オプションで指定できる値は次の 3 つです。

- オン: スペースを挿入します。
- オフ: スペースを削除します。
- 不確定: 元の書式設定のままにします。

さまざまなオプションの例を以下の表に示します。

| クラス定義のオプション | チェック済み | オフにした場合 |
| --- | --- | --- | 
| Insert space between a class declaration's name and bases list (クラス宣言の名前と基底クラス リストの間にスペースを挿入する) | `class X (object): pass` | `class X(object): pass` | 
| Insert space within bases list parentheses (基底クラス リストのかっこ内にスペースを挿入する) | `class X( object ): pass` | `class X(object): pass` |
| Insert space within empty bases list parentheses (空の基底クラス リストのかっこ内にスペースを挿入する) | `class X( ): pass` | `class X(): pass` |

<br/>

| 関数定義のオプション | チェック済み | オフにした場合 |
| --- | --- | --- |
| Insert space between a function declaration's name and parameter list (関数宣言の名前とパラメーター リストの間にスペースを挿入する) | `def X (): pass` | `def X(): pass` | 
| Insert space within parameter list parentheses (パラメーター リストのかっこ内にスペースを挿入する) | `def X( a, b ): pass` | `def X(a, b): pass` |
| Insert space within empty parameter list parentheses (空のパラメーター リストのかっこ内にスペースを挿入する) | `def X( ): pass` | `def X(): pass` |
| Insert spaces around '=' in default parameter values (既定のパラメーター値の '=' の前後にスペースを挿入する) | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Insert space before and after return annotation operators (リターン注釈演算子の前後にスペースを挿入する) | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| 演算子のオプション | チェック済み | オフにした場合 |
| --- | --- | --- |
| Insert spaces around binary operators (バイナリ演算子の前後にスペースを挿入する) | `a + b` | `a+b` |
| Insert spaces around assignments (代入演算子の前後にスペースを挿入する) | `a = b` | `a=b` |

<br/>

| 式のスペースのオプション | チェック済み | オフにした場合 |
| --- | --- | --- |
| Insert space between a function call's name and argument list (関数宣言の名前と引数リストの間にスペースを挿入する) | `X ()` | `X()` |
| 空の引数リストのかっこ内にスペースを挿入する | `X( )` | `X()` |
| 引数リストのかっこ内にスペースを挿入する | `X( a, b )` | `X(a, b)` |
| Insert space within parentheses of expression (式のかっこ内にスペースを挿入する) | `( a )` | `(a)` |
| Insert space within empty tuple parentheses (空のタプルのかっこ内にスペースを挿入する) | `( )` | `()` |
| Insert space within tuple parentheses (タプルのかっこ内にスペースを挿入する) | `( a, b )` | `(a, b)` |
| 空の角かっこ内にスペースを挿入する | `[ ]` | `[]` |
| Insert spaces within square brackets of lists (リストの角かっこ内にスペースを挿入する) | `[ a, b ]` | `[a, b]` |
| 始め角かっこの前にスペースを挿入する | `x [i]` | `x[i]` |
| 角かっこ内にスペースを挿入する | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>ステートメント

**[ステートメント]** オプションでは、さまざまなステートメントをより Python らしい形式に自動的に書き換えるかどうかを指定します。

| オプション | 書式設定前 | 書式設定後 |
| --- | --- | --- |
| Place imported modules on new line (インポートされたモジュールを新しい行に配置する) | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Remove unnecessary semicolons (不要なセミコロンを削除する) | `x = 42;` | `x = 42` |
| Place multiple statements on new lines (複数のステートメントを新しい行に配置する) | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |


## <a name="wrapping"></a>折り返し

**[折り返し]** では、**[コメントの最大幅]** (既定値は 80) を設定できます。 **[長すぎるコメントを折り返します]** オプションを設定した場合、その最大幅を超えるコメントは自動的に再フォーマットされます。

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```



## <a name="fill-comment-paragraph-command"></a>[Fill Comment Paragraph(コメント段落をページ幅に合わせる)] コマンド

**[編集] > [詳細設定] > [Fill Comment Paragraph (コメント段落をページ幅に合わせる)]** (Ctrl + E、P) を設定すると、コメント テキストがリフローおよび書式設定され、複数の短い行を 1 行にまとめたり長すぎる行を複数の行に分けたりできます。

例:

```python
# foo 
# bar
# baz
```

変更後:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

変更後:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
