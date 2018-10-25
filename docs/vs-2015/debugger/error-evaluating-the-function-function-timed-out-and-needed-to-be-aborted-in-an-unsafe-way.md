---
title: 'エラー: 関数の評価&#39;関数&#39;がタイムアウトし、安全でない方法で中止されるために必要な |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70c2276ef49ebc90deb6530b781856d9e9b2d29d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904534"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>エラー: 関数の評価&#39;関数&#39;タイムアウトしたため、安全でない方法で中止する必要があります。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

メッセージの全文: 関数 'function' の評価がタイムアウトし、安全でない方法で中止する必要があります。 これがターゲット プロセスを壊れている可能性があります。 

.NET オブジェクトの状態を検査しやすいように、デバッガーは (通常はプロパティの getter メソッドと ToString 関数) の追加のコードを実行するデバッグ対象のプロセスを自動的に強制されます。 ほとんどすべてのシナリオでは、これらの関数は、すぐに完了し、非常に簡単にデバッグします。 ただし、デバッガーは、サンド ボックスで、アプリケーションを実行しません。 その結果、プロパティ get アクセス操作子またはハングするネイティブ関数を呼び出す ToString メソッドは回復可能なことができない可能性がある、タイムアウトが長につながります。 このエラー メッセージが発生した場合は、この問題が発生します。
 
この問題の一般的な理由の 1 つは、デバッガーは、プロパティを評価するときのみできる検査を実行するスレッド。 したがって、プロパティが、デバッグ対象のアプリケーション内で実行するには、他のスレッドで待機している場合、および .NET ランタイムが中断することはない方法で待機している場合は、この問題が発生します。
 
## <a name="to-correct-this-error"></a>このエラーを解決するには
 
この問題を次の 3 つの考えられる解決策があります。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方法 1: プロパティの get アクセス操作子または ToString メソッドの呼び出しからデバッガーを防止します。
 
エラー メッセージでは、デバッガーを呼び出すしようとしました。 関数の名前を確認します。 この関数を変更する場合は、プロパティ get アクセス操作子または ToString メソッドの呼び出しからデバッガーを回避できます。 次のいずれかの操作を行います。
 
* 他の種類のプロパティ get アクセス操作子以外のコードにメソッドを変更するか、ToString メソッドと、問題が解消します。
    - または -
* (の ToString)DebuggerDisplay 属性を型に定義し、デバッガー以外の ToString を評価することができます。
    - または -
* (のプロパティ ゲッター)配置、`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`プロパティの属性。 API の互換性の理由から、プロパティを維持する必要があるメソッドがある場合に役立ちます。 が、メソッドが本当に必要です。
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>解決方法 2: 評価を中止するデバッガーを求める対象のコードがあります。
 
エラー メッセージでは、デバッガーを呼び出すしようとしました。 関数の名前を確認します。 かどうかは、プロパティ get アクセス操作子または ToString メソッドが正常に実行することがあります失敗し、特に状況では、問題を別のスレッドのコードを実行するコードする必要があります実装関数を呼び出すことができます`System.Diagnostics.Debugger.NotifyOfCrossThreadDependency`関数を中止するデバッガーを依頼するには。評価します。 このソリューションでは、明示的に、これらの関数を評価することも可能ですが、既定の動作は NotifyOfCrossThreadDependency 呼び出しが発生したときに実行を停止します。
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>解決方法 3: すべての暗黙的な評価を無効にします。
 
以前のソリューションで問題が解決しない場合に移動*ツール* / *オプション*、設定をオフにし、*デバッグ* /  *一般的な* / *プロパティの評価とその他の暗黙的な関数呼び出しを有効にする*します。 これは、ほとんどの暗黙的な関数の評価版ソフトウェアを無効にし、問題を解決する必要があります。



  




