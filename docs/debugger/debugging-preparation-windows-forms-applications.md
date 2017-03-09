---
title: "デバッグの準備 : Windows フォーム アプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "デバッグ [C#], Windows アプリケーション"
  - "デバッグ [J#], Windows アプリケーション"
  - "デバッグ [Visual Basic], Windows アプリケーション"
  - "デバッグ [Visual Studio], Windows アプリケーション"
  - "デバッグ (Windows アプリケーションを)"
  - "Windows アプリケーション, デバッグ"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# デバッグの準備 : Windows フォーム アプリケーション
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows フォーム プロジェクト テンプレートは、Windows フォーム アプリケーションを作成します。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] では、この種類のアプリケーションを簡単にデバッグできます。  詳細については、「[Creating a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
 プロジェクト テンプレートを使用して Windows フォーム プロジェクトを作成する場合、デバッグ構成とリリース構成に必要な設定は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって自動的に作成されます。  この設定は必要に応じて変更できます。  設定の変更は、**\[\<プロジェクト名\> プロパティ ページ\]** ダイアログ ボックス \(Visual Basic の場合は **\[My Project\]**\) で行います。  
  
 詳細については、「[プロパティの推奨設定](../debugger/managed-debugging-recommended-property-settings.md)」を参照してください。  
  
 推奨される追加のプロパティ設定を次の表に示します。  
  
### \[デバッグ\] タブの構成プロパティ  
  
|**プロパティ名**|**設定値**|  
|----------------|-------------|  
|**\[開始動作\]**|-   ほとんどの場合、**\[スタート プロジェクト\]** に設定します。  デバッグの開始時に他の実行可能ファイルを起動する場合 \(通常は DLL をデバッグする場合\) には、**\[外部プログラムの開始\]** に設定します。|  
  
 Windows フォーム アプリケーションは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内から、または既に実行中のアプリケーションにアタッチすることによってデバッグできます。  アタッチの詳細については、「[実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
### C\#、F\#、または Visual Basic の Windows フォーム アプリケーションをデバッグするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でプロジェクトを開きます。  
  
2.  必要に応じて、ブレークポイントを作成します。  
  
     Windows フォーム アプリケーションはイベント ドリブンであるため、ブレークポイントはイベント ハンドラー コード内またはイベント ハンドラー コードによって呼び出されるメソッド内に設定します。  ブレークポイントが配置される一般的なイベントは次のとおりです。  
  
    1.  Click、Enter などのコントロールに関連付けられたイベント。  
  
    2.  Load、Activated など、アプリケーションの起動またはシャットダウンに関連付けられたイベント。  
  
    3.  フォーカス イベントと検証イベント。  
  
     詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)」を参照してください。  
  
3.  **\[デバッグ\]** メニューの **\[開始\]** をクリックします。  
  
4.  「[デバッガーの基本事項](../debugger/debugger-basics.md)」で説明されている方法でデバッグします。  
  
## 参照  
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)   
 [C\#、F\#、および Visual Basic のプロジェクト](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [方法 : デバッグ構成とリリース構成を設定する](../debugger/how-to-set-debug-and-release-configurations.md)   
 [C\# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows フォーム](../Topic/Windows%20Forms.md)