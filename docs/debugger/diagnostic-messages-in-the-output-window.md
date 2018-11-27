---
title: 出力ウィンドウにメッセージを送信 |Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
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
ms.openlocfilehash: 02bdd2c6d83e13887a8051ab4101627ba14220fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724482"
---
# <a name="send-messages-to-the-output-window"></a>出力ウィンドウにメッセージを送信します。

実行時のメッセージを記述することができます、**出力**ウィンドウを使用して、<xref:System.Diagnostics.Debug>クラスまたは<xref:System.Diagnostics.Trace>に含まれるクラスの<xref:System.Diagnostics>クラス ライブラリ。 使用して、<xref:System.Diagnostics.Debug>クラスのみ出力をする場合、*デバッグ*プログラムのバージョン。 使用して、<xref:System.Diagnostics.Trace>クラスの両方で出力する場合、*デバッグ*と*リリース*バージョン。  
  
## <a name="output-methods"></a>出力メソッド  
 <xref:System.Diagnostics.Trace> クラスと <xref:System.Diagnostics.Debug> クラスが提供する出力方法は次のとおりです。  
  
- 各種の `Write` メソッド。実行を中断せずに情報を出力します。 これらのメソッドは、Visual Basic の以前のバージョンで使用されていた `Debug.Print` メソッドに代わるものです。  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>メソッドで、指定した条件が失敗した場合に実行し、出力の情報を中断します。 既定では、`Assert` メソッドはダイアログ ボックスに情報を出力します。 詳細については、次を参照してください。[マネージ コードでアサーション](../debugger/assertions-in-managed-code.md)します。  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>と<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>メソッドで、実行と出力の情報を常に中断します。 既定では、`Fail` メソッドはダイアログ ボックスに情報を出力します。  
  
**出力**ウィンドウに関する情報を表示できます。  
  
- デバッガーが読み込んだり、アンロードしたりしたモジュール  
  
- スローされた例外  
  
- 終了したプロセス  
  
- 終了したスレッド  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [[出力] ウィンドウ](../ide/reference/output-window.md)   
 [アプリケーションのトレースとインストルメント化](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#、 F#、および Visual Basic プロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)
