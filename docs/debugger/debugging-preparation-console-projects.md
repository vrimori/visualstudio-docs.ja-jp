---
title: "デバッグの準備 : コンソール プロジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
helpviewer_keywords: 
  - "コンソール アプリケーション, デバッグ"
  - "デバッグ [Visual Studio], コンソール アプリケーション"
  - "デバッグ (コンソール アプリケーションの)"
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# デバッグの準備 : コンソール プロジェクト
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コンソール プロジェクトのデバッグの準備は Windows プロジェクトのデバッグの準備に似ていますが、次の点を考慮する必要があります。  詳細については、「[Windows フォーム アプリケーション](../debugger/debugging-preparation-windows-forms-applications.md)」および「[Debugging Preparation: Windows Forms Applications \(.NET\)](http://msdn.microsoft.com/ja-jp/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)」を参照してください。  コンソール アプリケーションはどれも類似しているため、このトピックでは次のプロジェクトの種類について説明します。  
  
-   C\# コンソール アプリケーション  
  
-   Visual Basic コンソール アプリケーション  
  
-   C\+\+ コンソール アプリケーション \(.NET\)  
  
-   C\+\+ コンソール アプリケーション \(Win32\)  
  
 コンソール アプリケーションのコマンド ライン引数を指定する必要がある場合があります。  詳細については、「[C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)」、「[Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)」、または「[C\# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)」を参照してください。  
  
 すべてのプロジェクト プロパティと同様に、これらの引数はデバッグ セッション間および Visual Studio セッション間で保持されます。  このため、対象のコンソール アプリケーションを以前にデバッグしたことがある場合は、前回のセッションで \[**\<プロジェクト名\> プロパティ ページ**\] ダイアログ ボックスに入力した引数が存在する場合があります。  
  
 コンソール アプリケーションは、**\[コンソール\]** ウィンドウを使用して、入力を受け付けたり出力メッセージを表示したりします。  **コンソール** ウィンドウに書き込むには、アプリケーションで Debug オブジェクトではなく **Console** オブジェクトを使用する必要があります。  ただし、**Visual Studio の出力**ウィンドウに書き込むには、通常どおりに Debug オブジェクトを使用します。  アプリケーションの書き込み先を理解し、間違った場所でメッセージを探すことのないようにしてください。  詳細については、「[Console クラス](https://msdn.microsoft.com/en-us/library/system.console.aspx)」、「[Debug クラス](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx)」、および「[&#91;出力&#93; ウィンドウ](../ide/reference/output-window.md)」を参照してください。  
  
## アプリケーションの起動  
 いくつかのコンソール アプリケーションが起動すると、それらのアプリケーションは最後まで実行されてから終了します。  この動作のため、実行を中断してデバッグする時間が十分ない場合があります。  アプリケーションをデバッグできるようにするには、次のいずれかの手順に従ってアプリケーションを起動します。  
  
-   アプリケーションを起動し、ブレークポイントに達するまで実行する。  
  
-   アプリケーションを起動し、ソース コードの最初の行ですぐに中断する。  
  
-   ソース コード ウィンドウで、行を右クリックし、**\[カーソル行の前まで実行\]** をクリックする。  
  
     アプリケーションが起動され、選択した行まで実行されます。または、その行に達する前にブレークポイントがヒットした場合は、ブレークポイントまで実行されます。  
  
 コンソール アプリケーションをデバッグする場合、Visual Studio からではなく、コマンド プロンプトからアプリケーションを起動することもできます。  その場合は、コマンド プロンプトからアプリケーションを起動し、Visual Studio デバッガーをアプリケーションにアタッチします。  詳細については、「[実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
 Visual Studio からコンソール アプリケーションを起動すると、**\[コンソール\]** ウィンドウが Visual Studio ウィンドウの背後に表示される場合があります。  Visual Studio からコンソール アプリケーションを起動しようとしても、何も起こらない場合は、Visual Studio ウィンドウを移動してみてください。  
  
## 参照  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)   
 [Visual C\+\+ プロジェクトの種類](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C\#、F\#、および Visual Basic のプロジェクト](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)