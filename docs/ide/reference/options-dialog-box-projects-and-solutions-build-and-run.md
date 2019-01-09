---
title: '[ビルド/実行] ([オプション] ダイアログ ボックス - [プロジェクトおよびソリューション])'
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be6ac2a482e2e6fe52ad4458fec727f0da2dafe0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917797"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>[ビルド/実行] ([オプション] ダイアログ ボックス - [プロジェクトおよびソリューション])

このダイアログ ボックスで、同時にビルドできる Visual C++ または C# のプロジェクトの最大数、特定の既定のビルドの動作、およびいくつかのビルドのログ設定を指定することができます。 これらのオプションにアクセスするには、**[ツール]、[オプション]** の順に選択し、**[プロジェクトおよびソリューション]** を展開し、**[ビルド/実行]** を選択します。

**並行してビルドするプロジェクトの最大数**

同時にビルドできる Visual C++ および C# のプロジェクトの最大数を指定します。 ビルド プロセスを最適化するため、並列プロジェクトのビルドの最大数が、コンピューターの CPU 数に自動的に設定されます。 最大値は 32 です。

**実行時に、スタートアップ プロジェクトおよび依存関係のみをビルドする**

F5 キーを使用する場合にスタートアップ プロジェクトとその依存関係のみをビルドするには、**[デバッグ]、[開始]** メニュー コマンドの順に選択するか、または **[ビルド]** メニューの適用可能なコマンドを選択します。 何も選択しないと、すべてのプロジェクトと依存関係がビルドされます。

**実行時に、プロジェクトが最新の状態でないとき**

*"[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] プロジェクトだけで使用できます。"*

F5 キーを押すか、**[デバッグ]、[開始]** コマンドの順に選択してプロジェクトを実行するとき、プロジェクトの構成が最新の状態でない場合には、既定の設定 **[ビルドするかどうかを確認する]** でメッセージが表示されます。 実行のたびにプロジェクトをビルドするには、**[常にビルドする]** を選択します。 プロジェクト実行時のすべての自動ビルドを抑止するには、**[ビルドしない]** を選択します。

**実行時に、ビルドまたは配置のエラーが発生したとき**

*"[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] プロジェクトだけで使用できます。"*

F5 キーを押すか、**[デバッグ]、[開始]** コマンドの順に選択してプロジェクトを実行するとき、ビルドが失敗してもプロジェクトを実行する必要がある場合は、既定の設定 **[起動するかどうかを確認する]** でメッセージが表示されます。 **[古いバージョンを起動する]** を選択すると、最新の正常なビルドが自動的に起動されます。この結果として、実行コードとソース コードとの間に不一致が生じる可能性があります。 メッセージを抑止するには、**[起動しない]** を選択します。

**新しいソリューションでは現在選択されているプロジェクトをスタートアップ プロジェクトとして使用する**

このオプションを設定すると、新しいソリューションでは現在選択されているプロジェクトがスタートアップ プロジェクトとして使用されます。

**MSBuild プロジェクト ビルドの出力の詳細**

ビルドの **[出力]** ウィンドウで表示される情報量を決定します。

**MSBuild プロジェクト ビルド ログ ファイルの詳細**

*"[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] プロジェクトだけで使用できます。"*

ビルド ログ ファイルに書き込まれる情報量を決定します。ビルド ログ ファイルは、\\...\\*ProjectName*\Debug\\*ProjectName*.log にあります。

## <a name="see-also"></a>関連項目

- [コードのコンパイルとビルド](../../ide/compiling-and-building-in-visual-studio.md)
- [[オプション] ダイアログ ボックス、[プロジェクトおよびソリューション]](projects-and-solutions-options-dialog-box.md)
- [[オプション] ダイアログ ボックス、[プロジェクトおよびソリューション]、[Web プロジェクト]](options-dialog-box-projects-and-solutions-web-projects.md)