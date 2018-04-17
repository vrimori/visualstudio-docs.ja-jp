---
title: 'エラー: 関数の評価&#39;関数&#39;タイムアウトしたため、安全でない方法で中止するために必要な |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c230c27c8d1c8dcc01910fa598fb8a97b314845
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>エラー: 関数の評価&#39;関数&#39;タイムアウトしたため、安全でない方法で中止するために必要

メッセージの全文: タイムアウトしたため、安全でない方法で中止するために必要な関数 'function' を評価します。 ターゲット プロセスを破損この可能性があります。 

.NET オブジェクトの状態を検査しやすいように、デバッガーが自動的に強制するには、追加コード (通常プロパティ get アクセス操作子メソッドと ToString 関数) を実行するデバッグ対象のプロセスです。 ほとんどすべてのシナリオでは、これらの関数は、短時間で完了し、非常に簡単にデバッグします。 ただし、デバッガーは、サンド ボックスで、アプリケーションを実行しません。 その結果、プロパティ get アクセス操作子または ToString を呼び出すメソッドに対してがハングするネイティブ関数には回復できない可能性がある長いタイムアウトにつながります。 このエラー メッセージが発生すると、これが発生しました。
 
この問題の一般的な理由の 1 つは、デバッガーは、プロパティを評価するときのみできる、スレッドを実行する、調査対象です。 したがって、プロパティが、デバッグ対象のアプリケーション内で実行するには、他のスレッドで待機している場合、および .NET ランタイムが中断することはない方法で待機している場合は、この問題が発生します。
 
## <a name="to-correct-this-error"></a>このエラーを解決するには
 
この問題を次の 3 つの考えられる解決策があります。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方法 1: プロパティの get アクセス操作子または ToString メソッドの呼び出しからデバッガーを防止します。
 
エラー メッセージでは、デバッガーが、呼び出すしようとしています。 関数の名前を指定します。 この関数を変更する場合は、プロパティ get アクセス操作子または ToString メソッドの呼び出しからデバッガーができなくなります。 次のいずれかの操作を行います。
 
* メソッドを他の何らかの種類のプロパティ get アクセス操作子以外のコードに変更するか、ToString メソッドと、問題が解消します。
    - または -
* (の ToString)DebuggerDisplay 属性型を定義、および ToString 以外のものを評価するデバッガーを持つことができます。
    - または -
* プロパティ getter を含まない) (Put、`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`プロパティの属性です。 これは、API 互換性の理由から、プロパティを維持する必要があるメソッドがある場合に役立ちますが、メソッドにする必要があります。
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>評価を中止するデバッガーを依頼ターゲット コードがある解決方法 2。
 
エラー メッセージでは、デバッガーが、呼び出すしようとしています。 関数の名前を指定します。 ToString メソッド、プロパティ get アクセス操作子が失敗する正常に実行するかどうかは、特に状況では、問題をコードは別のスレッドのコードを実行する必要があるし、実装関数を呼び出すことができます`System.Diagnostics.Debugger.NotifyOfCrossThreadDependency`に関数を中止するデバッガーを確認してください。評価します。 このソリューションでは、明示的にこれらの関数を評価することも可能であるけれども、既定の動作は NotifyOfCrossThreadDependency 呼び出しが発生したときに実行を停止します。
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>解決方法 3: すべての暗黙的な評価を無効にします。
 
以上の解決策で問題が解決しない場合に、*ツール* > *オプション*、設定をオフにし、*デバッグ* >  *一般的な* > *プロパティの評価とその他の暗黙的な関数呼び出しを有効にする*です。 これにより、ほとんどの暗黙的な関数評価を無効にし、問題を解決する必要があります。



  
