---
title: 'ワークフロー デザイナー - 方法: ワークフロー内のブレークポイントの設定'
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
ms.openlocfilehash: a1d7dcb437a77bd91c8dbb3360a33c7260fabb91
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755240"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>方法: ワークフロー内のブレークポイントの設定

ワークフロー デザイナーを使用して、Visual Basic または c# コードでの操作と同様、グラフィカル ワークフローにブレークポイントを設定することができます。 設定したそれぞれのブレークポイントで、ワークフローの実行が停止します。

ブレークポイントが 3 つの状態:*保留*、*バインド*、および*エラー*します。 ブレークポイントは、設定時には "保留" になり、穴のない赤いアイコンで表示されます。 特定の種類のワークフローがランタイムによって読み込まれると、ブレークポイントの状態は "バインド" になります。 不適切な形式のブレークポイントを指定した場合 (アクティビティ名が無効など) は、エラー ウィンドウが表示されます。 ブレークポイントはブレークポイント ウィンドウに追加されますが、小さな x 印が付きます。

> [!NOTE]
> 呼び出されるワークフローに対してブレークポイントを設定することはできません。

> [!NOTE]
> オプションを選択するようにして**を有効にする マイ コードのみ (マネージのみ)** から、**ツール** > **オプション** > **デバッグ**メニューをデバッグする前にします。 オプションが選択されていない、別のシーケンス内で入れ子になった 2 つのシーケンスがあると目の内部シーケンスにブレークポイントを設定すると、次のようにキーを押して**F11**を 2 つ目の内部シーケンスにはデバッグできません。

> [!NOTE]
> XAML ファイルのプロパティへの完全パスが正確でない場合、ワークフロー内のブレークポイントはヒットしません。 XAML ファイルに完全なパスは、プロジェクトまたはソリューションを別のフォルダーに、または別のコンピューターに移動した後は正確ではありません。 選択**Ctrl**+**S**を保存し、完全なパスのプロパティを更新します。

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>デザイン ビューでアクティビティにブレークポイントを設定するには

1. デバッガーを中断する位置にあるアクティビティを選択します。

2. **デバッグ**メニューの **ブレークポイントの切り替え**します。 アクティビティの左上端に赤色のアイコンが表示されます。

   または、キー **F9**するか、アクティビティを選択することができます、アクティビティを右クリックし、選択した後**ブレークポイント** > **ブレークポイントの挿入**コンテキスト メニュー。

## <a name="see-also"></a>関連項目

- [ワークフロー デバッガーを呼び出す方法](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [ワークフロー デザイナーを使用したワークフローのデバッグ](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [方法: ワークフロー デザイナーを使用して XAML をデバッグする](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)