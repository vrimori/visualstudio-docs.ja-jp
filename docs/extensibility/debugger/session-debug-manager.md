---
title: セッション マネージャーのデバッグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 001c0b954cd47b9825a6982f2474d6fd6d415e23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="session-debug-manager"></a>セッションのデバッグ マネージャー
セッションのデバッグ マネージャー (SDM) は、任意の数の任意の数のマシンの数にかかわらず複数のプロセスでプログラムをデバッグするデバッグ エンジン (DE) を管理します。 マルチプレクサー デバッグ エンジンだけでなく、SDM は IDE に、デバッグ セッションの統一されたビューを提供します。  
  
## <a name="session-debug-manager-operation"></a>セッションのデバッグ マネージャーの操作  
 セッションのデバッグ マネージャー (SDM) は、DE を管理します。 同時に、マシンで実行されている 1 つ以上のデバッグ エンジンである可能性があります。 DEs を多重送信するには、は、SDM は、DEs からインターフェイスの数をラップし、それらを 1 つのインターフェイスとして IDE に公開します。  
  
 パフォーマンスを向上させるには、一部のインターフェイスはいない多重化されます。 代わりに、DE から直接使用して、これらのインターフェイスへの呼び出しが、SDM を通過しません。 たとえば、メモリ、コード、およびドキュメントのコンテキストで使用するインターフェイスは多重化されない、特定の命令、メモリ、または特定 DE では、デバッグ、特定のプログラムでドキュメントを参照しているためです。 その他の DE をそのレベルの通信に関与する必要はありません。  
  
 これは、すべてのコンテキストの該当しません。 式の評価コンテキストのインターフェイスを呼び出し、SDM を通過します。 式の評価中に、SDM のラップ、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)する可能性のある、同じプロセス内のプログラムのデバッグは、複数の DEs が生じる可能性がありますその式が評価されるときにあるため、IDE をすることで、インターフェイス同じスレッドで実行されています。  
  
 委任メカニズムとして、SDM が通常は機能が、ブロードキャスト機構を果たす場合があります。 たとえば、式の評価中に指定されたスレッドでコードを実行できることをすべて DEs を通知する、ブロードキャスト機構として、SDM は機能します。 同様に、SDM 停止イベントを受信すると、それらを停止することを実行しているすべてのプログラムにブロードキャストします。 ステップが呼び出されたときに、SDM にブロードキャストするすべてのプログラム実行を続行することができます。 ブレークポイントはもすべて DE にブロードキャストされます。  
  
 現在のプログラム、スレッド、またはスタック フレーム、SDM を追跡しません。 プロセス、プログラム、およびスレッド情報が特定のデバッグ イベントと共に SDM に送信します。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガー コンポーネント](../../extensibility/debugger/debugger-components.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)