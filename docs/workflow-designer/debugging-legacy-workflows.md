---
title: "従来のワークフローのデバッグ |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4898e8f720143bd60337c9fe6bed20a7489c0d04
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="debugging-legacy-workflows"></a>従来のワークフローのデバッグ

使用するかどうかは、従来の Windows ワークフロー デザイナーで[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]をビルドする[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]target.NET Framework 3.0 または 3.5 をデバッグできるその他のプログラムと同様に、ワークフローのブレークポイントの設定、プロセスへのアタッチを調べることでアプリケーションスレッドと呼び出し履歴。 また、リモート デバッグを実行することもできます。

> [!NOTE]
> コンピューターに複数のバージョンの Visual Studio をインストールしてアンインストールした場合、WF3 のデバッグは失敗し、次のいずれかが発生する可能性があります。
>
> -   ブレークポイントがヒットしません。
> -   次のメッセージが表示されます。
>
> **Web サーバーでデバッグを開始できません。デバッガーが正しくインストールされていません。要求された種類のコードがデバッグできません。セットアップを実行してインストールするか、デバッガーを修復します。**
>
> .NET Framework 3.0 または 3.5 のワークフローのデバッグ時にこれらのシナリオのいずれかが発生する場合は、Visual Studio インストールの修復を実行してください。

 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] は、次のような標準の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッグ ウィンドウに統合されています。

-   **ブレークポイント**: 想定どおりに動作しますが、関数名のアクティビティを指定します。

-   **呼び出し履歴**: ワークフロー インスタンス内で実行されたアクティビティの概要を変更します。 内のエントリ、**呼び出し履歴**ウィンドウは、実行されるアクティビティの深さ優先検索します。 エントリをダブルクリックすると、選択したアクティビティにフォーカスを設定できます。

-   **スレッド**: デバッグ中は、ワークフロー インスタンスのインスタンス ID を提供します。

 Visual Studio for Windows Workflow Foundation は、次のデバッグ機能をサポートしません。

-   デザイナ画面上の条件付きブレークポイント

-   クイック ウォッチ

-   次のステートメントの設定

-   カーソル行の前まで実行

-   エディット コンティニュ

-   ジャスト イン タイム デバッグ

-   混合モードのデバッグ