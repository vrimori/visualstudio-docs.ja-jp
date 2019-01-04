---
title: ワークフロー デザイナー - 方法。変数デザイナーを使用する
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b7df8f03444a0205c5628bbd36f249d68b43ad7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824342"
---
# <a name="how-to-use-the-variable-designer"></a>方法: 変数デザイナーを使用する

変数デザイナーは、データ バインディングや条件ステートメントで使用する変数を作成するために使用します。 デザイナーにアクセスする をクリックして、**変数**デザイン キャンバスの左下隅のボタンをクリックします。 デザイナーには、表形式で表示され、以外の各列見出しで並べ替えることができますを変数の一覧が含まれています、**既定**列。 それぞれの変数には、名前、変数の型、スコープ、および既定値 (存在する場合) があります。 名前および既定値は編集可能なテキスト フィールドで、型およびスコープはドロップダウン リストです。 スコープは、変数デザイナーの呼び出し時に選択されたアクティビティです。 選択したスコープ内に変数を作成できない場合は、対応するスコープに変数を作成できる直近の先祖アクティビティが既定のスコープとなります。 詳細については、次を参照してください。[変数と引数 (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)します。

 いずれかの並べ替えコントロールをユーザーが明示的に使用するか、変数デザイナーを閉じてから開き直すか、または、別の変数を作成するまで、並べ替え順序は適用されません。

## <a name="to-create-a-new-variable"></a>新しい変数を作成するには

1.  Visual Studio では、ワークフローまたはアクティビティ ソリューションを開きます。

2.  デザイン キャンバスで、ワークフローのアクティビティを選択します。

3.  変数デザイナーを開く をクリックして、**変数**デザイン キャンバスの左下隅のボタンをクリックします。 変数デザイナーが表示されます。

4.  というラベルの付いた空の行をクリックします。**変数の作成**です。 これには、次の既定値を使用して新しい変数新しい行を追加するが: の variablex、**名前**x は一意の変数名を作成する自動的にインクリメントされる 1 の初期値を持つ整数**文字列**の**変数の型**、および**シーケンス**の**スコープ**します。 値は追加されません**既定**します。 これらの値は、ワークフローのデザイン プロセス中にいつでも変更できます。

    > [!NOTE]
    > 変数を削除するをクリックして、変数を選択し、キーを押します、**削除**キー。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーの使用](developing-applications-with-the-workflow-designer.md)
- [変数と引数](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [方法: 引数デザイナーを使用します。](../workflow-designer/how-to-use-the-argument-designer.md)