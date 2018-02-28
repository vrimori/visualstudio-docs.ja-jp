---
title: "JavaScript 構文エラー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-syntax-errors"></a>JavaScript 構文エラー
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]構文エラーが発生したときの 1 つの構造、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]ステートメントでは、1 つ以上の構文上のルールに違反しています。  
  
## <a name="errors"></a>エラー  
  
|エラー番号|説明|  
|------------------|-----------------|  
|1019|['break' をループの外に設定できません。](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|['continue' をループの外に設定できません。](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[条件付きコンパイルは無効になっています。](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' は 'switch' ステートメントのなかに、一度のみ表示できます。](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[予想 ' ('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[予想 ')'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[予想 '/'](../../javascript/misc/expected-minus.md)|  
|1003|[':' が必要です。](../../javascript/misc/expected-colon.md)|  
|1004|[';' が必要です。](../../javascript/misc/expected-semicolon.md)|  
|1032|['@' が必要です。](../../javascript/misc/expected-at.md)|  
|1029|['@end' が必要です。](../../javascript/misc/expected-at-end.md)|  
|1007|[予想 ' &#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|['{' が必要です](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|['}' が必要です](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|['=' が必要です。](../../javascript/misc/expected-equal-javascript.md)|  
|1033|['catch' が必要です](../../javascript/misc/expected-catch.md)|  
|1031|[定数が必要です。](../../javascript/misc/expected-constant.md)|  
|1023|[16 進数の数字が必要です。](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[識別子が必要です。](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[識別子、文字列、または数値が必要です](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|['while' が必要です](../../javascript/misc/expected-while.md)|  
|1014|[無効な文字](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[このラベルが定義されていません。](../../javascript/misc/label-not-found.md)|  
|1025|[ラベルが再定義されました](../../javascript/misc/label-redefined.md)|  
|1018|['return' ステートメントが関数の外にあります。](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[構文エラー](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Throw ステートメントに指定する式は、ソース コードの同一行に記述してください](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[未終了のコメントです。](../../javascript/misc/unterminated-comment.md)|  
|1015|[未終了の文字列定数](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>スクリプト ホスト エラー  
 次のエラーは、スクリプト ホストに関連するエラーを話している正しくが可能性がありますがたまにそれら。  
  
|エラー|HRESULT|説明|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|エラーは、スクリプト エンジンとホスト間で渡される記録されています。 ホストは、呼び出し元に、エラー コードを渡す必要があります。|  
|SCRIPT_E_REPORTED|0x80020101|スクリプト エンジンには、IActiveScriptSite::OnScriptError を介してホストにハンドルされない例外が報告されました。 ホストは、このエラーを無視することができます。|  
|SCRIPT_E_PROPAGATE|0x8002010|スクリプト エラーは、別のスレッドで可能性のある呼び出し元に反映中です。 ホストは、呼び出し元に、エラー コードを渡す必要があります。|  
  
## <a name="see-also"></a>関連項目  
 [JavaScript ランタイム エラー](../../javascript/reference/javascript-run-time-errors.md)