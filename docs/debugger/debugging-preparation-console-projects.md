---
title: 'デバッグの準備: コンソール プロジェクト |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfaf36da772165a4f35e984dff117c6ec41ca60f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150952"
---
# <a name="debugging-preparation-console-projects"></a>デバッグの準備 : コンソール プロジェクト
コンソール プロジェクトのデバッグの準備は Windows プロジェクトのデバッグの準備に似ていますが、次の点を考慮する必要があります。 詳細については、次を参照してください。 [Windows フォーム アプリケーション](../debugger/debugging-preparation-windows-forms-applications.md)、および[デバッグの準備: Windows フォーム アプリケーション (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)します。 コンソール アプリケーションはどれも類似しているため、このトピックでは次のプロジェクトの種類について説明します。  
  
-   C# コンソール アプリケーション  
  
-   Visual Basic コンソール アプリケーション  
  
-   C++ コンソール アプリケーション (.NET)  
  
-   C++ コンソール アプリケーション (Win32)  
  
 コンソール アプリケーションのコマンド ライン引数を指定する必要がある場合があります。 詳細については、次を参照してください[C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)、 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)、または[c# デバッグ構成のプロジェクトの設定](../debugger/project-settings-for-csharp-debug-configurations.md)。  
  
 すべてのプロジェクト プロパティと同様に、これらの引数はデバッグ セッション間および Visual Studio セッション間で保持されます。 そのため、コンソール アプリケーションを以前にデバッグした場合は、注意してくださいで入力した以前のセッションから引数が存在する可能性があります、 **\<プロジェクト > プロパティ ページ** ダイアログ ボックス。  
  
 コンソール アプリケーションを使用して、**コンソール**ウィンドウへの入力と出力メッセージを表示します。 書き込む、**コンソール**ウィンドウで、アプリケーションを使用する必要があります、**コンソール**Debug オブジェクトではなくオブジェクト。 書き込む、 **Visual Studio の出力**ウィンドウで、通常どおりに Debug オブジェクトを使用します。 アプリケーションの書き込み先を理解し、間違った場所でメッセージを探すことのないようにしてください。 詳細については、次を参照してください。[コンソール クラス](/dotnet/api/system.console)、 [Debug クラス](/dotnet/api/system.diagnostics.debug)、および[出力ウィンドウ](../ide/reference/output-window.md)します。  
  
## <a name="starting-the-application"></a>アプリケーションの起動  
 いくつかのコンソール アプリケーションが起動すると、それらのアプリケーションは最後まで実行されてから終了します。 この動作のため、実行を中断してデバッグする時間が十分ない場合があります。 アプリケーションをデバッグできるようにするには、次のいずれかの手順に従ってアプリケーションを起動します。  
  
-   アプリケーションでは、実行を開始し、ブレークポイントに到達するまで実行されます。  
  
-   アプリケーションを起動し、ソース コードの最初の行ですぐに中断する。  
  
-   ソース コード ウィンドウでは、行を右クリックして**カーソルまで実行**します。  
  
     アプリケーションが起動され、選択した行まで実行されます。または、その行に達する前にブレークポイントがヒットした場合は、ブレークポイントまで実行されます。  
  
 コンソール アプリケーションをデバッグする場合、Visual Studio からではなく、コマンド プロンプトからアプリケーションを起動することもできます。 その場合は、コマンド プロンプトからアプリケーションを起動し、Visual Studio デバッガーをアプリケーションにアタッチします。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
 Visual Studio からコンソール アプリケーションを起動すると、**コンソール**ウィンドウが Visual Studio ウィンドウの背後に見える場合があります。 Visual Studio からコンソール アプリケーションを起動しようとしても、何も起こらない場合は、Visual Studio ウィンドウを移動してみてください。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 
  [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [Visual C++ プロジェクトの種類](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)