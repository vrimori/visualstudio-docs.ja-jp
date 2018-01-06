---
title: "出力ウィンドウに診断メッセージを送信 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: df071834a6ae36da0156c527284f6ffbfcee0e4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>出力ウィンドウに診断メッセージを送信します。
実行時のメッセージを記述することができます、**出力**ウィンドウを使用して、`Debug`クラスまたは`Trace`に含まれるクラスの<xref:System.Diagnostics>クラス ライブラリです。 プログラムのデバッグ バージョンだけで出力する場合は Debug クラスを使用します。 プログラムのデバッグ バージョンとリリース バージョンの両方で出力する場合は Trace クラスを使用します。  
  
## <a name="output-methods"></a>出力メソッド  
 <xref:System.Diagnostics.Trace> クラスと <xref:System.Diagnostics.Debug> クラスが提供する出力方法は次のとおりです。  
  
-   各種の `Write` メソッド。実行を中断せずに情報を出力します。 これらのメソッドは、Visual Basic の以前のバージョンで使用されていた `Debug.Print` メソッドに代わるものです。  
  
-   <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> メソッドと <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> メソッド。指定された条件を満たさない場合は、実行を中断して情報を出力します。 既定では、`Assert` メソッドはダイアログ ボックスに情報を出力します。 詳細については、次を参照してください。[マネージ コードのアサーション](../debugger/assertions-in-managed-code.md)です。  
  
-   <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> メソッドと <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> メソッド。常に実行を中断して情報を出力します。 既定では、`Fail` メソッドはダイアログ ボックスに情報を出力します。  
  
 出力だけでなく、アプリケーションから、**出力**ウィンドウに関する情報も表示できます。  
  
-   デバッガーが読み込んだり、アンロードしたりしたモジュール  
  
-   スローされた例外  
  
-   終了したプロセス  
  
-   終了したスレッド  
  
## <a name="see-also"></a>参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [[出力] ウィンドウ](../ide/reference/output-window.md)   
 [アプリケーションのトレースとインストルメント](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)