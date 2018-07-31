---
title: 出力ウィンドウに診断メッセージを送信 |Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27cec31b775ba5f8d201c81cbd65f5b161353986
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252298"
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>出力ウィンドウに診断メッセージを送信します。
実行時のメッセージを記述することができます、**出力**ウィンドウを使用して、<xref:System.Diagnostics.Debug>クラスまたは<xref:System.Diagnostics.Trace>に含まれるクラスの<xref:System.Diagnostics>クラス ライブラリ。 使用して、<xref:System.Diagnostics.Debug>クラスだけで出力する場合、*デバッグ*プログラムのバージョン。 使用して、<xref:System.Diagnostics.Trace>クラスの両方で出力する場合、*デバッグ*と*リリース*バージョン。  
  
## <a name="output-methods"></a>出力メソッド  
 <xref:System.Diagnostics.Trace> クラスと <xref:System.Diagnostics.Debug> クラスが提供する出力方法は次のとおりです。  
  
-   各種の `Write` メソッド。実行を中断せずに情報を出力します。 これらのメソッドは、Visual Basic の以前のバージョンで使用されていた `Debug.Print` メソッドに代わるものです。  
  
-   <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> メソッドと <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> メソッド。指定された条件を満たさない場合は、実行を中断して情報を出力します。 既定では、`Assert` メソッドはダイアログ ボックスに情報を出力します。 詳細については、次を参照してください。[マネージ コードでアサーション](../debugger/assertions-in-managed-code.md)します。  
  
-   <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> メソッドと <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> メソッド。常に実行を中断して情報を出力します。 既定では、`Fail` メソッドはダイアログ ボックスに情報を出力します。  
  
 アプリケーションから、out プログラムだけでなく、**出力**ウィンドウに関する情報も表示できます。  
  
-   デバッガーが読み込んだり、アンロードしたりしたモジュール  
  
-   スローされた例外  
  
-   終了したプロセス  
  
-   終了したスレッド  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [[出力] ウィンドウ](../ide/reference/output-window.md)   
 [アプリケーションのトレースとインストルメント](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 
  [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)
