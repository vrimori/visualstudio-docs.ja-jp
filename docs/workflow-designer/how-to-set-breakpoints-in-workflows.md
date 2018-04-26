---
title: 'ワークフロー デザイナー - 方法: ワークフロー内のブレークポイントを設定'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2ef863bfb899c218a65673236c284bed63aed11
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-set-breakpoints-in-workflows"></a>方法 : ワークフロー内のブレークポイントを設定する

Windows ワークフロー デザイナーを使用する場合は、Visual Basic または c# のコードで行うよう、グラフィカル ワークフローにブレークポイントを設定することができます。 設定したそれぞれのブレークポイントで、ワークフローの実行が停止します。

 ブレークポイントが 3 つの状態:*保留*、*バインド*、および*エラー*です。 ブレークポイントは、設定時には "保留" になり、穴のない赤いアイコンで表示されます。 特定の種類のワークフローがランタイムによって読み込まれると、ブレークポイントの状態は "バインド" になります。 不適切な形式のブレークポイントを指定した場合 (アクティビティ名が無効など) は、エラー ウィンドウが表示されます。 ブレークポイントはブレークポイント ウィンドウに追加されますが、小さな x 印が付きます。

> [!NOTE]
> 呼び出されるワークフローに対してブレークポイントを設定することはできません。

> [!WARNING]
> オプションを選択することを確認してください **[マイ コードのみ (マネージのみ)** から、**ツール**、**オプション**、**デバッグ**する前に] メニュー。デバッグします。 別のシーケンス内で入れ子になった 2 つのシーケンスがあり、最初の内部シーケンスにブレークポイントを設定する場合、以下のキーを押して**F11**場合、2 つ目の内部シーケンスにステップインしません、 **マイ コードのみ (マネージのみ)** オプションが選択されていません。

> [!WARNING]
> XAML ファイルのプロパティへの完全パスが正確でない場合、ワークフロー内のブレークポイントにヒットしません。XAML ファイルへの完全パスは、プロジェクトやソリューションを別のフォルダーや別のコンピューターへ移動すると正確ではなくなります。Ctrl キーを押しながら S キーを押すと、完全パスのプロパティが保存および更新されます。

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>デザイン ビューでアクティビティにブレークポイントを設定するには

1.  デバッガーを中断する位置にあるアクティビティを選択します。

2.  **デバッグ**メニューの **ブレークポイントの切り替え**です。 アクティビティの左上端に赤色のアイコンが表示されます。

     または、ショートカット キーも**F9**キーをアクティビティを右クリックし、選択するか、アクティビティを選択すると**ブレークポイント**し**ブレークポイントの挿入**、コンテキスト メニュー。

## <a name="see-also"></a>関連項目

- [ワークフロー デバッガーを呼び出す方法](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [ワークフロー デザイナーを使用したワークフローのデバッグ](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [方法: ワークフロー デザイナーを使用して XAML をデバッグする](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)