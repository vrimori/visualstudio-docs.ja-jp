---
title: セッション デバッグ マネージャー |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 014ac5b4c310b97fb1c041eeaededef8c97ab88b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905359"
---
# <a name="session-debug-manager"></a>セッション デバッグ マネージャー
セッション デバッグ マネージャー (SDM) は、任意の数の任意の数のマシン間で任意の数の複数のプロセスでプログラムをデバッグするデバッグ エンジン (DE) を管理します。 マルチプレクサーのデバッグ エンジンだけでなく、SDM は IDE に、デバッグ セッションの統合ビューを提供します。  
  
## <a name="session-debug-manager-operation"></a>セッション デバッグ マネージャーの操作  
 セッション デバッグ マネージャー (SDM) は、DE を管理します。 1 つ以上のデバッグ エンジンを同時に、マシンで実行されていることができます。 DEs を多重化するには、は、SDM は、数、DEs からインターフェイスをラップし、1 つのインターフェイスとして IDE を許すことにします。  
  
 パフォーマンスを向上させるのにはいくつかのインターフェイスは多重化されます。 代わりに、DE から直接メッセージが表示され、これらのインターフェイスへの呼び出しは、SDM を経由しません。 たとえば、メモリ、コード、およびドキュメントのコンテキストで使用されるインターフェイスは多重化、特定の命令、メモリ、または特定のドイツでは、デバッグ、特定のプログラムでドキュメントを参照しているため、します。 その他の DE をそのレベルの通信に関与する必要はありません。  
  
 すべてのコンテキストの場合は true ではありません。 式の評価コンテキストのインターフェイスを呼び出し、SDM を通過します。 式の評価中に、SDM のラップ、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)可能性があるのと同じプロセス内でプログラムのデバッグは複数の DEs 可能性がありますが含まれるその式が評価されるため、IDE が提供されるインターフェイス同じスレッドで実行されています。  
  
 通常、SDM が委任メカニズムとして機能しますが、ブロードキャスト機構を果たすことがあります。 たとえば、式の評価中に指定されたスレッドでコードを実行できることをすべて DEs を通知するブロードキャスト メカニズムとして、SDM が機能します。 同様に、SDM 停止イベントを受け取るときに、プログラムの実行を停止する必要があります をブロードキャストします。 ステップが呼び出されたときに、SDM にブロードキャストする、プログラム実行を継続できます。 ブレークポイントは、すべて DE にもブロードキャストします。  
  
 現在のプログラム、スレッド、またはスタック フレーム、SDM を追跡しません。 プロセス、プログラム、およびスレッドの情報は、特定のデバッグ イベントと共に SDM に送信されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)