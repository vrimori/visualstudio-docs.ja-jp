---
title: エラー :関数の評価&#39;関数&#39;がタイムアウトし、安全でない方法で中止されるために必要な |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a72bd821d7ecd32e82b2ad3b02debe03ff511531
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883312"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>エラー :関数の評価&#39;関数&#39;タイムアウトしたため、安全でない方法で中止する必要があります。

完全なメッセージ テキスト:関数 'function' の評価がタイムアウトし、安全でない方法で中止される必要がありました これがターゲット プロセスを壊れている可能性があります。 

.NET オブジェクトの状態を検査しやすいように、デバッガーは (通常はプロパティの getter メソッドと ToString 関数) の追加のコードを実行するデバッグ対象のプロセスを自動的に強制されます。 ほとんどすべてのシナリオでは、これらの関数は、すぐに完了し、非常に簡単にデバッグします。 ただし、デバッガーは、サンド ボックスで、アプリケーションを実行しません。 その結果、プロパティ get アクセス操作子またはハングするネイティブ関数を呼び出す ToString メソッドは回復可能なことができない可能性がある、タイムアウトが長につながります。 このエラー メッセージが発生した場合は、この問題が発生します。
 
この問題の一般的な理由の 1 つは、デバッガーは、プロパティを評価するときのみできる検査を実行するスレッド。 したがって、プロパティが、デバッグ対象のアプリケーション内で実行するには、他のスレッドで待機している場合、および .NET ランタイムが中断することはない方法で待機している場合は、この問題が発生します。
 
## <a name="to-correct-this-error"></a>このエラーを解決するには
 
この問題をいくつかの考えられる解決策があります。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方法 1デバッガーのプロパティの get アクセス操作子または ToString メソッドの呼び出しを防ぐ
 
エラー メッセージでは、デバッガーを呼び出すしようとしました。 関数の名前を確認します。 この関数を変更する場合は、プロパティ get アクセス操作子または ToString メソッドの呼び出しからデバッガーを回避できます。 次のいずれかの操作を行います。
 
* 他の種類のプロパティ get アクセス操作子以外のコードにメソッドを変更するか、ToString メソッドと、問題が解消します。
    - または -
* (の ToString)DebuggerDisplay 属性を型に定義し、デバッガー以外の ToString を評価することができます。
    - または -
* (のプロパティ ゲッター)配置、`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`プロパティの属性。 API の互換性の理由から、プロパティを維持する必要があるメソッドがある場合に役立ちます。 が、メソッドが本当に必要です。
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>解決方法 2評価を中止するデバッガーを求める対象のコードがあります。
 
エラー メッセージでは、デバッガーを呼び出すしようとしました。 関数の名前を確認します。 かどうかは、プロパティ get アクセス操作子または ToString メソッドが正常に実行することがあります失敗し、特に状況では、問題を別のスレッドのコードを実行するコードする必要があります実装関数を呼び出すことができます`System.Diagnostics.Debugger.NotifyOfCrossThreadDependency`関数を中止するデバッガーを依頼するには。評価します。 このソリューションでは、明示的に、これらの関数を評価することも可能ですが、既定の動作は NotifyOfCrossThreadDependency 呼び出しが発生したときに実行を停止します。
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>解決方法 3すべての暗黙的な評価を無効にします。
 
以前のソリューションで問題が解決しない場合に移動**ツール** > **オプション**、設定をオフにし、**デバッグ** >  **一般的な** > **プロパティの評価とその他の暗黙的な関数呼び出しを有効にする**します。 これは、ほとんどの暗黙的な関数の評価版ソフトウェアを無効にし、問題を解決する必要があります。

### <a name="solution-4-enable-managed-compatibility-mode"></a>ソリューション(&S)マネージ互換モードを有効にします。

従来のデバッグ エンジンに切り替えると、このエラーを回避できる可能性があります。 移動して**ツール** > **オプション**、設定を選択および**デバッグ** > **全般** > **マネージ互換モードを使う**します。 詳細については、次を参照してください。[デバッグ オプション全般](../debugger/general-debugging-options-dialog-box.md)します。
