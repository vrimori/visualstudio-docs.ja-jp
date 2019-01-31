---
title: エラー :コードでターゲット プロセスが終了しました&#39;コード&#39;関数の評価中に&#39;関数&#39;|Microsoft Docs
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbd7a4c9b3f1524e3552ea7c0c2dd636b09c0f2b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967314"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>エラー :コードでターゲット プロセスが終了しました&#39;コード&#39;関数の評価中に&#39;関数&#39;

完全なメッセージ テキスト:関数 'function' の評価中にターゲット プロセスがコード 'code' で終了しました

.NET オブジェクトの状態を検査しやすいように、デバッガーは自動的に強制的に追加のコードを実行するデバッグ対象のプロセス (通常はプロパティの getter メソッドおよび`ToString`関数)。 ほとんどのシナリオでこれらの関数が正常に完了またはデバッガーでキャッチできる例外をスローします。 ただし、状況によっては、カーネルの境界を越える、ユーザー メッセージ ポンプが必要かが回復可能な例外はキャッチできないがあります。 結果をプロパティ get アクセス操作子またはコードを実行する ToString メソッドとしてどちらかが明示的にプロセスを終了します (などを呼び出す`ExitProcess()`) かキャッチできない、未処理の例外をスローします (たとえば、 `StackOverflowException`) は終了、デバッグ対象のプロセスと、デバッグ セッションを終了します。 このエラー メッセージが発生した場合は、この問題が発生します。
 
この問題の一般的な理由の 1 つは、デバッガーには、自身を呼び出すプロパティが評価されると、でも、スタック オーバーフロー例外を発生可能性がありますがこれです。 スタック オーバーフロー例外を回復することはできませんし、ターゲット プロセスは終了します。
 
## <a name="to-correct-this-error"></a>このエラーを解決するには
 
この問題を 2 つの考えられる解決策があります。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方法 1デバッガーのプロパティの get アクセス操作子または ToString メソッドの呼び出しを防ぐ 

エラー メッセージでは、デバッガーを呼び出そうとする関数の名前を確認します。 関数の名前からには、その関数が再評価を試すことができます、**イミディ エイト**評価をデバッグするウィンドウ。 評価するときにデバッグが可能な**イミディ エイト**ウィンドウからの暗黙的な評価とは異なり、**自動変数/ローカル/ウォッチ**windows、未処理の例外でデバッガーが中断されます。

この関数を変更する場合は、呼び出し元のプロパティの get アクセス操作子からデバッガーを回避できますまたは`ToString`メソッド。 次のいずれかの操作を行います。
 
* 他の種類のプロパティ get アクセス操作子以外のコードにメソッドを変更するか、ToString メソッドと、問題が解消します。
    - または -
* (の`ToString`) を定義する、`DebuggerDisplay`属性型には、デバッガー以外の何かの評価を持つことができます`ToString`します。
    - または -
* (のプロパティ ゲッター)配置、`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`プロパティの属性。 API の互換性の理由から、プロパティを維持する必要があるメソッドがある場合に役立ちますが、メソッドが本当に必要です。

このメソッドを変更することはできません、代替命令にターゲット プロセスを中断し、評価を再試行することができます。
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>解決方法 2すべての暗黙的な評価を無効にします。
 
以前のソリューションで問題が解決しない場合に移動**ツール** > **オプション**、設定をオフにし、**デバッグ** >  **一般的な** > **プロパティの評価とその他の暗黙的な関数呼び出しを有効にする**します。 これは、ほとんどの暗黙的な関数の評価版ソフトウェアを無効にし、問題を解決する必要があります。
