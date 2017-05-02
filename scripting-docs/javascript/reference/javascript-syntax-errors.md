---
title: "JavaScript 構文エラー | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "エラー [JavaScript]"
  - "構文エラー、JavaScript"
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# JavaScript 構文エラー
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 構文エラーはいずれかの [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ステートメントの構造が構文規則に違反した場合に発生します。  
  
## エラー  
  
|エラー番号|説明|  
|-----------|--------|  
|1019|['break' はループの外に設定できません](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|['continue' はループの外に設定できません](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[条件付きコンパイルは無効になっています。](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' は 'switch' ステートメントで 1 度しか使用できません](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|['\(' が必要です](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|['\)' が必要です](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|['\/' が必要です](../../javascript/misc/expected-minus.md)|  
|1003|[':' が必要です](../../javascript/misc/expected-colon.md)|  
|1004|[';' が必要です](../../javascript/misc/expected-semicolon.md)|  
|1032|['@' が必要です](../../javascript/misc/expected-at.md)|  
|1029|['@end' が必要です](../../javascript/misc/expected-at-end.md)|  
|1007|['&#93;' が必要です](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|['{' が必要です](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|['}' が必要です](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|['\=' が必要です](../../javascript/misc/expected-equal-javascript.md)|  
|1033|['catch' が必要です](../../javascript/misc/expected-catch.md)|  
|1031|[定数が必要です](../../javascript/misc/expected-constant.md)|  
|1023|[16 進数の数字が必要です](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[識別子が必要です](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[識別子、文字列、または数値が必要です](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|['while' が必要です](../../javascript/misc/expected-while.md)|  
|1014|[無効な文字です](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[ラベルが見つかりません](../../javascript/misc/label-not-found.md)|  
|1025|[ラベルが再定義されました](../../javascript/misc/label-redefined.md)|  
|1018|['return' ステートメントが関数の外にあります](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[構文エラーです](../../javascript/misc/syntax-error-javascript.md)|  
|1035|['throw' ステートメントに指定する式は、ソース コードの同一行に記述してください](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[未終了のコメントです](../../javascript/misc/unterminated-comment.md)|  
|1015|[未終了の文字列定数です](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### スクリプト ホスト エラー  
 次のエラーは、正確に言えばスクリプト ホストに関連するエラーですが、ときどき発生することがあります。  
  
|エラー|HRESULT|説明|  
|---------|-------------|--------|  
|SCRIPT\_E\_RECORDED|0x86664004|エラーは、スクリプト エンジンとホスト間で渡すために記録されています。  ホストは、呼び出し元にエラー コードを渡す必要があります。|  
|SCRIPT\_E\_REPORTED|0x80020101|スクリプト エンジンが IActiveScriptSite::OnScriptError を使用して、ハンドルされない例外をホストに報告しました。  ホストはこのエラーを無視できます。|  
|SCRIPT\_E\_PROPAGATE|0x8002010|スクリプト エラーは呼び出し元に反映されます。呼び出し元は異なるスレッドにあることもあります。  ホストは、呼び出し元にエラー コードを渡す必要があります。|  
  
## 参照  
 [JavaScript ランタイム エラー](../../javascript/reference/javascript-run-time-errors.md)