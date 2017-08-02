---
title: "Visual Studio での Python コードのリファクタリング | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ebcb29-72d1-4958-9a63-8984c03d5c22
caps.latest.revision: 1
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
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: ea69604524010ab794a4de0e85aea1e5fd680ac4
ms.lasthandoff: 04/10/2017

---

# <a name="refactoring-python-code"></a>Python コードのリファクタリング

Visual Studio には、Python ソース コードの変換とクリーンアップを自動的に実行するためのいくつかのコマンドが用意されています。

- [[名前の変更]](#rename) は、選択したクラス、メソッド、または変数の名前を変更します
- [[メソッドの抽出]](#extract-method) は、選択したコードから新しいメソッドを作成します
- [[インポートの追加]](#add-import) は、不足しているインポートを追加するためのスマート タグを提供します
- [[Remove unused imports (使用されていないインポートの削除)]](#remove-imports) は、使用されていないインポートを削除します

<a name="rename-variable"</a>
## <a name="rename"></a>名前の変更

1. 名前を変更する識別子を右クリックして、**[名前の変更]** を選択します。または、その識別子にキャレットを置き、**[編集] > [リファクター] > [名前の変更]** メニューを選択するか F2 キーを押します。
1. 表示された **[名前の変更]** ダイアログで、識別子の新しい名前を入力し、**[OK]** を選択します。

  ![新しい識別子名を入力するための [名前の変更] プロンプト](~/python/media/code-refactor-rename-1.png)

1. その次のダイアログで、名前変更を適用するコード内のファイルとインスタンスを選択します。特定の変更をプレビューするには、個別のインスタンスを選択します。

  ![変更の適用場所を選択するための [名前の変更] ダイアログ](~/python/media/code-refactor-rename-2.png)

1. **[適用]** を選択して、ソース コード ファイルを変更します。 これは取り消し可能なアクションです。

## <a name="extract-method"></a>メソッドの抽出

1. 別のメソッドに抽出するコード行または式を選択します。
1. **[編集] > [リファクター] > [メソッドの抽出]** メニュー コマンドを選択するか、Ctrl + R、M キーを押します。
1. 表示されるダイアログ ボックスで新しいメソッドの名前を入力し、抽出先を指定して、クロージャ変数を選択します。 クロージャに選択されなかった変数はメソッド引数に返されます。

  ![[メソッドの抽出] ダイアログ](~/python/media/code-refactor-extract-method-1.png)

1. **[OK]** を選択すると、指定に従ってコードが変更されます。

  ![メソッドの抽出の効果](~/python/media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>インポートの追加

型情報のない識別子にキャレットを置くと、スマート タグ (コードの左側の電球アイコン) が表示され、そのコマンドを使用して必要な `import` または `from ... import` ステートメントを追加できます。

![[インポートの追加] スマート タグ](~/python/media/code-refactor-add-import-1.png)

`import` の入力候補は、現在のプロジェクト内の最上位レベルのパッケージおよびモジュールと標準ライブラリに対して提供されます。`from ... import` の入力候補は、サブモジュールおよびサブパッケージとモジュール メンバーに対して提供されます。 これには関数、クラス、またはエクスポートされたデータが含まれます。 いずれかの選択肢を選択すると、そのステートメントがファイル上部の他のインポートの後に追加されるか、同じモジュールが既にインポートされている場合は既存の `from ... import` ステートメント内に挿入されます。

![インポートの追加の結果](~/python/media/code-refactor-add-import-2.png)

Visual Studio は、モジュール内で実際に定義されていないメンバーを除外しようとします (別のモジュール内にインポートされたが、インポートを行うモジュールの子ではないモジュールなど)。 たとえば、多くのモジュールが `from xyz import sys` ではなく `import sys` を使用するため、モジュールに `sys` を除外する `__all__` メンバーがなくても、他のモジュールから `sys` をインポートするための入力候補が表示されません。

同様に、Visual Studio は他のモジュールまたは組み込みの名前空間からインポートされる関数を除外します。 たとえば、あるモジュールが `sys` モジュールから `settrace` 関数をインポートする場合、理論的にはそのモジュールから関数をインポートすることもできます。 しかし、`import settrace from sys` を直接使用する方法が最良であるため、Visual Studio はそのステートメントを明確に提示します。

さらに、上記のルールに従って除外すべき候補が、(たとえば名前がモジュール内の値に割り当てられているなどの理由で) 表示対象となる他の値を含んでいる場合でも、Visual Studio はそのインポートを除外します。 これは、その値が別のモジュールで定義されており、追加で割り当てるとエクスポートされないダミーの値になる可能性があるため、その値をエクスポートすべきではないということを前提としています。

<a name="remove-imports"</a>
## <a name="remove-unused-imports"></a>使用されていないインポートの削除

コードの作成では、モジュールの `import` ステートメントが最終的にまったく使われないことがよくあります。 Visual Studio はコードを分析するので、インポートされた名前が `import` ステートメントの出現箇所より下のスコープ内で使用されているかどうかを調べて、import ステートメントが必要かどうかを自動的に判断できます。

エディター内の任意の場所を右クリックして **[Remove Imports (インポートの削除)]** を選択すると、**[すべてのスコープ]** または **[Current Scope (現在のスコープ)]** のいずれかを選択できます。

![[Remove imports (インポートの削除)] メニュー](~/python/media/code-refactor-remove-imports-1.png)

Visual Studio によってコードが適切に変更されます。

![インポートの削除の効果](~/python/media/code-refactor-remove-imports-2.png)

Visual Studio は制御フローを考慮しないことに注意してください。`import` ステートメントの前に名前を使用した場合、その名前は実際に使用されたものとして扱われます。 また、Visual Studio はすべての `from __future__` インポート、クラス定義の内部で実行されるインポート、`from ... import *` ステートメントから実行されるインポートを無視します。
