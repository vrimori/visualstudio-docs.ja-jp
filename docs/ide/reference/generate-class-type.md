---
title: Visual Studio でクラスまたは型を生成する
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 67e6e8744672c35bdf13e30269297dcc52c50a04
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929609"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Visual Studio でクラスまたは型を生成する

このコード生成は以下に適用されます。

- C#

- Visual Basic

**機能:** クラスまたは型のコードをすぐに生成できます。

**条件:** 新しいクラスまたは型を導入し、自動的に適切に宣言したいとき。

**理由:** クラスまたは型は使用する前に自分で宣言できますが、この機能ではクラスまたは型が自動的に生成されます。

## <a name="how-to"></a>方法

1. 赤い波線が表示されている行にカーソルを置きます。 赤い波線は、まだ存在していないクラスを示します。

   - C#: 

       ![強調表示された C# のコード](media/class-highlight-cs.png)

   - Visual Basic: 

       ![強調表示された VB のコード](media/class-highlight-vb.png)

2. 次に、以下のいずれかを実行します。

   - **キーボード**
      - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   - **マウス**
      - 右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。
      - 赤い波線をポイントし、表示された ![電球](media/bulb-cs.png) アイコンをクリックします。
      - テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

      ![クラス生成のプレビュー](media/class-preview-cs.png)

3. ドロップダウン メニューからいずれかのオプションを選択します。

   - [新しいファイルにクラス '*TypeName*' を生成する] &mdash; *TypeName* という名前のクラスを *TypeName*.cs/.vb という名前のファイルに作成します。
   - [クラス '*TypeName*' を生成する] &mdash; *TypeName* という名前のクラスを現在のファイルに作成します。
   - [入れ子クラス '*TypeName*' を生成する] &mdash; 現在のクラス内に入れ子になった *TypeName* という名前のクラスを作成します。
   - [新しい型の生成] &mdash; 指定したすべてのプロパティを持つ新しいクラスまたは構造体を作成します。

   > [!TIP]
   > プレビュー ウィンドウの下部にある **[変更のプレビュー]** リンクを使うと、選択する前に、行われる[すべての変更を確認する](../../ide/preview-changes.md)ことができます。

4. **[新しい型の生成]** 項目を選択した場合、**[型の生成]** ダイアログ ボックスが開きます。 新しい型のアクセシビリティ、種類、および場所を構成します。

   ![型の生成](media/class-newtype-cs.png)

   選択ツール | 説明
   --- | ---
   アクセス | 型に *[既定]*、*[内部]*、または *[パブリック]* アクセスを設定します。
   種類 | *[クラス]* または *[構造体]* として設定できます。
   name | 変更できません。入力済みの名前になります。
   プロジェクト | ソリューションに複数のプロジェクトがある場合、クラス/構造体を置くプロジェクトを選択できます。
   ファイル名 | 新しいファイルを作成することも、既存のファイルに型を追加することもできます。

クラスまたは構造体が作成されます。 C# の場合、コンストラクターも作成されます。

- C#

   ![クラス生成の結果 C#](media/class-result-cs.png)

- Visual Basic

   ![クラス生成の結果 VB](media/class-result-vb.png)

## <a name="see-also"></a>関連項目

- [コード生成](../code-generation-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)