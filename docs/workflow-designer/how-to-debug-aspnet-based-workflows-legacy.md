---
title: "方法: ASP.NET ベースのワークフロー (レガシ) のデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0eb248f04119f8f0ad70b9a09a4fb22c73399233
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>方法: ASP.NET ベースのワークフローをデバッグする (レガシ)
このトピックでは、従来の [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]で、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] ベースの [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] アプリケーションをデバッグする方法について説明します。  
  
 ワークフローをそのホストとなるプロセスにアタッチすることにより、ASP.NET で開始される従来のワークフロー、または Web サービスとして公開される従来のワークフローをデバッグすることができます。  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>ASP.NET ベースのワークフローをデバッグするには  
  
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
  
9. **[アタッチ]**をクリックします。  
  
10. ブラウザで既定の Web ページを開いて、ワークフローを開始します。  
  
## <a name="see-also"></a>関連項目  
 [Windows Workflow Foundation (レガシ) 用の Visual Studio デバッガーを起動](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [方法: ワークフロー (レガシ) 内のブレークポイントを設定](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)