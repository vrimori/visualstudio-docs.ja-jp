---
title: ワークフロー デザイナー - 方法。引数デザイナーを使用する
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88d9d568a115680c545a32a0d5f533fcab51da1f
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684601"
---
# <a name="how-to-use-the-argument-designer"></a>方法: 引数デザイナーを使用する

.NET Framework の以前のバージョンと比較して、引数デザイナー簡単にデータを入出力アクティビティ フローを許可します。 デザイナーにアクセスする をクリックして、**引数**デザイン キャンバスの左下隅のボタンをクリックします。 デザイナーには、表形式で表示され、以外の各列見出しで並べ替えることができますを引数のリストが含まれています、**既定値**列。 各引数には、名前、方向 (入力、出力、入力/出力、またはプロパティ)、型、および既定の式の値 (存在する場合) が含まれます。 名前および既定の式の値は編集可能なテキスト フィールドで、型および方向はドロップダウンです。 詳細については、次を参照してください。[変数と引数 (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)します。

## <a name="to-create-a-new-argument"></a>新しい引数を作成するには

1.  Visual Studio では、ワークフローまたはアクティビティ ソリューションを開きます。

2.  クリックして、引数デザイナーを開き、**引数**デザイン キャンバスの左下隅のボタンをクリックします。 引数デザイナーが表示されます。

3.  というラベルの付いた空の行をクリックします。**引数の作成**です。 これは、新しい行が次の既定値を使用して新しい引数を指定して追加されます: の argumentx、**名前**x は一意の引数の名前を作成する自動的にインクリメントされる 1 の初期値を持つ整数**で**の**方向**、および**文字列**の**引数の型**します。 値は追加されません**既定値**します。 これらの値は、ワークフローのデザイン プロセス中にいつでも変更できます。

    > [!NOTE]
    > 引数を削除するをクリックして、引数を選択し、キーを押します、**削除**キー。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーの使用](developing-applications-with-the-workflow-designer.md)
- [変数と引数](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)