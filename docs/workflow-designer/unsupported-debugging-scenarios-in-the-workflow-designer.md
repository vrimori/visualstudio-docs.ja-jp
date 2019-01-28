---
title: ワークフロー デザイナーでサポートされていないデバッグ シナリオ
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a93547bfb76459655f0b7fb896709ef880d84476
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009974"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>ワークフロー デザイナーでサポートされていないデバッグ シナリオ

.NET Framework 4 では、ワークフロー デザイナーは、多くの新機能を追加しますが、まだがサポートされていないいくつかのデバッグ シナリオがあります。

次に、サポートされていないワークフロー デザイナーのデバッグ シナリオを示します。

-   コードを編集した後では実行を続行できません。

-   ワークフローの任意の場所から実行を続行することはできません (次の設定)。

-   カーソルが到達するまで実行を続行できません (カーソル行の前まで実行)。

-   デザイナーを使用せずにコード内に作成されたワークフローをデバッグするためにワークフロー デザイナーを使用することはできません。

-   .NET Framework 4 のデザイナーでは、以前のバージョンの Windows Workflow Foundation (WF) で作成されたワークフローをデバッグできません。

-   アクティビティまたは <xref:System.Activities.Statements.Flowchart> ノード間のリンクにブレークポイントを定義することはできません。

-   クリップボードは、デバッグ時には使用できません。

-   アクティビティをコピーまたは貼り付けた場合にはブレークポイントは保持されません。

-   ワークフローのブレークポイントを呼び出し履歴ウィンドウに設定することはできません。

-   デザイナーでブレークポイントを作成するときに、**行**と**文字**の設定、**新しいブレークポイント**ダイアログは使用されません。

-   [ブレークポイント] ウィンドウまたはショートカット メニューは、ワークフローのデバッグで、次の列またはオプションをサポートしていません。

    -   状態

    -   ヒット カウント

    -   ヒット時 

    -   関数

    -   データ

    -   プロセス

    -   逆アセンブルを表示