---
title: ワークフロー デザイナー - 方法。インポート デザイナーを使用する
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a358ca4fbc6ffdfb1cf88aa42750e1d31cabb37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959240"
---
# <a name="how-to-use-the-imports-designer"></a>方法: インポート デザイナーを使用する

インポート デザイナーを使用すると、式で使用する型の名前空間を入力できます。 ほぼ同じように、**インポート**または**を使用して**単に完全修飾ではなく、式の型名を入力することで、Visual Basic および c#、インポート デザイナーで名前空間を指定するキーワードを使用します。バージョンの型名。

インポート デザイナーでは、UI での変更とワークフローの保存時に行われる変更の両方に応じて処理を行います。 ワークフローの保存時に、インポート デザイナーに名前空間を自動的に追加できます。 次に例を示します。

- 変数および引数の宣言で使用されている型の名前空間。

- 式で使用されている型の名前空間。

- ワークフローをシリアル化するために必要な、上記以外の名前空間 (ワークフロー内で削除されたカスタム アクティビティで使用した名前空間など)。

  ワークフローを保存すると、手動で削除したいくつかの名前空間がインポート デザイナーに自動的に再度追加されることがあります。これは、上記の一覧で説明したロジックによるものです。

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>名前空間をインポートされた名前空間の一覧に追加するには

1.  Visual Studio または再ホストされたワークフロー アプリケーションでは、WCF ワークフロー サービス アプリケーション、ワークフロー コンソール アプリケーション、またはアクティビティ ライブラリ プロジェクトを開きます。

2.  クリックして**Imports**メイン キャンバスの下部にあります。 インポート デザイナーが表示されます。

3.  名前空間を入力するか、インポート デザイナーの上部にあるドロップダウン リスト コントロールから名前空間を選択します。

     入力すると、入力した文字に一致する有効な名前空間の一覧が表示されます。

4.  キーを押して**Enter**一覧に、名前空間を追加します。

5.  一覧から名前空間を削除する場合は、名前空間を選択し、キーを押します、**削除**キーボードのキー。 名前空間が削除できるのは、たとえば、名前空間を含むアセンブリがプロジェクトによって参照されなくなる場合など、名前空間がなんらかの理由で無効である場合のみであることに注意してください。