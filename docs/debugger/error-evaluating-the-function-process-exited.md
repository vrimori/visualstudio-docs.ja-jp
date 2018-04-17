---
title: 'エラー: 関数の評価中にターゲット プロセスが終了して&#39;関数&#39;|Microsoft ドキュメント'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: reference
f1_keywords:
- vs.debug.error.process_exit_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8dd6f0f47eb7160198d59e788096613da85e22f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="error-the-target-process-exited-while-evaluating-the-function-39function39"></a>エラー: 関数の評価中にターゲット プロセスが終了して&#39;関数&#39;

メッセージの全文: 関数 'function' を評価中にターゲット プロセスが終了しました。 ターゲット プロセスの終了コードは、出力ウィンドウを参照してください。

.NET オブジェクトの状態を検査しやすいように、デバッガーが自動的に強制する追加のコードを実行するデバッグ対象のプロセス (通常はプロパティ get アクセス操作子メソッドおよび`ToString`関数)。 ほとんどのシナリオでこれらの関数は正常に完了またはデバッガーでキャッチできる例外をスローします。 ただし、状況によってはカーネルの境界を越える、ユーザー メッセージ ポンプを必要とまたは回復することはないため、例外をキャッチすることはできませんがあります。 結果、プロパティ get アクセス操作子またはコードを実行する ToString メソッドとしてどちらかが明示的にプロセスを終了します (たとえば、呼び出し`ExitProcess()`) またはキャッチできませんした未処理の例外をスローした (たとえば、 `StackOverflowException`) が終了されます、デバッグ対象のプロセスと、デバッグ セッションを終了します。 このエラー メッセージが発生すると、これが発生しました。
 
この問題の 1 つの一般的な理由は、こと、デバッガーには、自身を呼び出すプロパティが評価されると、これが原因で、スタック オーバーフロー例外です。 スタック オーバーフロー例外を回復することはできませんし、ターゲット プロセスは終了します。
 
## <a name="to-correct-this-error"></a>このエラーを解決するには
 
この問題を次の 2 つの考えられる解決策があります。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方法 1: プロパティの get アクセス操作子または ToString メソッドの呼び出しからデバッガーを防止します。 

エラー メッセージでは、デバッガーを呼び出そうとする関数の名前を指定します。 関数の名前を持つことができますしようとする再からその関数の評価、**イミディ エイト**評価をデバッグするウィンドウです。 評価するときにデバッグが可能な**イミディ エイト**ウィンドウのためからの暗黙的な評価とは異なり、**自動変数/ローカル/ウォッチ**windows で、デバッガーが未処理の例外で停止します。

この関数を変更できますを防ぐことができます、デバッガー プロパティ getter を呼び出すまたは`ToString`メソッドです。 次のいずれかの操作を行います。
 
* メソッドを他の何らかの種類のプロパティ get アクセス操作子以外のコードに変更するか、ToString メソッドと、問題が解消します。
    - または -
* (の`ToString`) を定義する、`DebuggerDisplay`属性型には、デバッガー以外の何かの評価を持つことができます`ToString`です。
    - または -
* プロパティ getter を含まない) (Put、`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`プロパティの属性です。 これは、API 互換性の理由から、プロパティのままにしておく必要があるメソッドがある場合に役立ちますが、メソッドにする必要があります。

このメソッドを変更することはできない場合、は、代替命令にターゲット プロセスを中断し、評価を再試行することができます。
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>解決方法 2:、すべての暗黙の評価が無効にします。
 
以上の解決策で問題が解決しない場合に、**ツール** > **オプション**、設定をオフにし、**デバッグ** >  **一般的な** > **プロパティの評価とその他の暗黙的な関数呼び出しを有効にする**です。 これにより、ほとんどの暗黙的な関数評価を無効にし、問題を解決する必要があります。



  
