---
title: 出力ウィンドウの診断メッセージ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72d9da2ea3ab6cb9807fc7e0a668155d37110c3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246795"
---
# <a name="diagnostic-messages-in-the-output-window"></a>出力ウィンドウの診断メッセージ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Diagnostics> クラス ライブラリに含まれている Debug クラスまたは Trace クラスを使用して、[出力] ウィンドウに出力されるランタイム メッセージを記述できます。 プログラムのデバッグ バージョンだけで出力する場合は Debug クラスを使用します。 プログラムのデバッグ バージョンとリリース バージョンの両方で出力する場合は Trace クラスを使用します。  
  
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
 [アプリケーションのトレースとインストルメント](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [インストルメンテーションとトレースの概要](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)



