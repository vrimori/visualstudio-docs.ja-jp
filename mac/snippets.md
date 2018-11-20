---
title: コード スニペット
description: Visual Studio for Mac でコード スニペットを利用して効率的にプログラミングする方法
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: a2db4477b0258159c867aa1219f858040d2efb26
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295373"
---
# <a name="code-snippets"></a>コード スニペット

コード スニペット (" _コード テンプレート_" と呼ばれることがよくあります) は、あらかじめ記述されているコード ブロックを挿入して編集できるので、効率的にプログラミングできます。 コード スニペットを使用すると、よく使うパターンを簡単に追加したり、開発者が構文をよく知らないときに新しいパターンを学習したりするのに便利です。 C#、F#、HTML、XML、Python、Razor のテンプレートが用意されています。

このセクションでは、スニペットを作成し、コードに挿入して使う方法について説明します。

## <a name="inserting-a-snippet"></a>スニペットの挿入

コード スニペットを追加するにはいくつかの方法があり、以下ではその一部を説明します。

* **タブ展開** - テンプレート名の入力を開始し、一覧からテンプレートを選び **、****Tab** キーを押して追加します。

  ![コードでのタブ展開](media/source-editor-image13.png)

* **ツールボックス** - ツールボックス パッドを使ってすべてのコード スニペットの一覧を表示します。 ツールボックスからソース コード内の正しい位置にテンプレートをドラッグします。

  ![ツールボックスでのコード スニペット](media/source-editor-image14.png)

* **テンプレート挿入コマンド** - 現在、テンプレートの挿入に対する既定のキー バインド セットはありません。 1 つ作成するには、**[Visual Studio] > [ユーザー設定] > [キー バインディング]** の順に移動して、`template` を検索します。 これにより、[バインディングの編集] フィールドに目的のキー バインドを追加することができ、 **[適用]** をクリックします。

  ![テンプレート挿入コマンド](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>新しいテンプレートの作成

さまざまな言語の多くの既存テンプレートを使って編集できますが、**[Visual Studio] > [ユーザー設定] > [テキスト エディター] > [コード スニペット]** で新しいテンプレートを追加することもできます。

![新しいテンプレートの挿入](media/source-editor-image12.png)

## <a name="see-also"></a>関連項目

* [コード スニペット (Windows の Visual Studio)](/visualstudio/ide/code-snippets)