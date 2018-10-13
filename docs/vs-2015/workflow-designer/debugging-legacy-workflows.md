---
title: 従来のワークフローのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8e35b16d10bf59b4ae8c91de2a5281d540c0e67c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210601"
---
# <a name="debugging-legacy-workflows"></a>従来のワークフローのデバッグ
[!INCLUDE[wfd1](../includes/wfd1-md.md)] の従来の [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]を使用して、.NET Framework 3.0 または 3.5 を対象とする [!INCLUDE[wf](../includes/wf-md.md)] アプリケーションを作成する場合は、ブレークポイントの設定、プロセスへのアタッチ、スレッドと呼び出しスタックの検査を実行して、他のプログラムと同じようにワークフローをデバッグできます。 また、リモート デバッグを実行することもできます。  
  
> [!NOTE]
>  コンピューターに複数のバージョンの Visual Studio をインストールしてアンインストールした場合、WF3 のデバッグは失敗し、次のいずれかが発生する可能性があります。  
>   
>  -   ブレークポイントがヒットしません。  
> -   次のメッセージが表示されます。  
>   
>  **Web サーバーでデバッグを開始できません。デバッガーが正しくインストールされていません。要求された種類のコードがデバッグできません。デバッガーをインストールまたはセットアップを実行します。**  
>   
>  .NET Framework 3.0 または 3.5 のワークフローのデバッグ時にこれらのシナリオのいずれかが発生する場合は、Visual Studio インストールの修復を実行してください。  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] は、次のような標準の [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] デバッグ ウィンドウに統合されています。  
  
-   **ブレークポイント**: 想定どおりに機能するが、関数名のアクティビティを指定します。  
  
-   **呼び出し履歴**: ワークフロー インスタンス内で実行されたアクティビティの概要を提供するよう変更します。 内のエントリ、**呼び出し履歴**ウィンドウが実行されるアクティビティの深さ優先検索します。 エントリをダブルクリックすると、選択したアクティビティにフォーカスを設定できます。  
  
-   **スレッド**: デバッグ中にワークフロー インスタンスのインスタンス ID を提供します。  
  
 Visual Studio for Windows Workflow Foundation は、次のデバッグ機能をサポートしません。  
  
-   デザイナ画面上の条件付きブレークポイント  
  
-   クイック ウォッチ  
  
-   次のステートメントの設定  
  
-   カーソル行の前まで実行  
  
-   エディット コンティニュ  
  
-   ジャスト イン タイム デバッグ  
  
-   混合モードのデバッグ  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio Debugger for Windows Workflow Foundation の起動 (レガシ)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Visual Studio Debugger for Windows Workflow Foundation の無効化 (レガシ)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [方法: ASP.NET ベースのワークフローをデバッグする (レガシ)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [方法: ワークフロー内にブレークポイントを設定する (レガシ)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [リモート コンピューターからのワークフローのデバッグ (レガシ)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [デバッグのステップ実行オプション (レガシ)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [方法: デバッグのステップ実行オプションを変更する (レガシ)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)