---
title: 'ワークフロー デザイナー - 方法: ASP.NET ベースのワークフロー (レガシ) のデバッグ'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7bf16a6a88c5d4cd063f1c32ca846031d8b2588d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975873"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>方法: ASP.NET ベースのワークフローをデバッグする (レガシ)

このトピックをターゲットとするか、.NET Framework version 3.5 または従来の Windows ワークフロー デザイナーで WinFX は、ASP.NET ベースの Windows Workflow Foundation (WF) アプリケーションをデバッグする方法について説明します。

ワークフローをそのホストとなるプロセスにアタッチすることにより、ASP.NET で開始される従来のワークフロー、または Web サービスとして公開される従来のワークフローをデバッグすることができます。

## <a name="to-debug-an-aspnet-based-workflow"></a>ASP.NET ベースのワークフローをデバッグするには

1.  設定して、ASP.NET アプリケーションのデバッグを有効にする**デバッグ = true** web.config ファイルにします。

2.  ワークフロー ライブラリをスタートアップ プロジェクトとして設定し、ワークフローのブレークポイントを設定します。

3.  ワークフロー プロジェクトのプロパティに既定の Web ページの URL を入力**デバッグ**オプション**外部 URL を使用してブラウザーを開始**テキスト ボックス。

4.  選択**プロセスにアタッチする**上、**デバッグ**メニュー。

5.  アタッチするプロセスを選択、**選択可能なプロセス** ボックスの一覧です。

     ワークフローのホストとなる w3wp.exe、webdev.webserver、または aspnet_wp プロセスにアタッチします。

6.  をクリックして**選択** の横に、 **Attach To**テキスト ボックス。

     **コードの種類の選択** ダイアログ ボックスが表示されます。

7.  選択**コードの種類をデバッグ**選択**ワークフロー**です。

8.  **[OK]** をクリックします。

9. **[アタッチ]** をクリックします。

10. ブラウザで既定の Web ページを開いて、ワークフローを開始します。

## <a name="see-also"></a>関連項目

- [Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [方法: ワークフロー内にブレークポイントを設定する (レガシ)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)