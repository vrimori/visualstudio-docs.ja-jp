---
title: セッション デバッグ マネージャー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0c3bb1ce939ed54997d8d8b40de75bcd095e4dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759146"
---
# <a name="session-debug-manager"></a>セッション デバッグ マネージャー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

セッション デバッグ マネージャー (SDM) は、任意の数の任意の数の任意の数のマシンで複数のプロセスでプログラムをデバッグするデバッグ エンジン (DE) を管理します。 マルチプレクサーのデバッグ エンジンだけでなく、SDM は IDE に、デバッグ セッションの統合ビューを提供します。  
  
## <a name="session-debug-manager-operation"></a>セッション デバッグ マネージャーの操作  
 セッション デバッグ マネージャー (SDM) は、DE を管理します。 同時に、マシンで実行されている 1 つ以上のデバッグ エンジンである可能性があります。 DEs を多重化するには、は、SDM は、数、DEs からインターフェイスをラップし、1 つのインターフェイスとして IDE を許すことにします。  
  
 パフォーマンスを向上させるのにはいくつかのインターフェイスは多重化されません。 代わりに、DE から直接メッセージが表示され、これらのインターフェイスへの呼び出しは、SDM を通過しません。 たとえば、メモリ、コード、およびドキュメントのコンテキストで使用されるインターフェイスはいないとして、特定の命令、メモリ、または特定のドイツでは、デバッグ、特定のプログラムでドキュメントを参照しているためで多重化されます。 その他の DE をそのレベルの通信に関与する必要はありません。  
  
 すべてのコンテキストの場合は true ではありません。 式の評価コンテキストのインターフェイスを呼び出し、SDM を通過します。 式の評価中に、SDM のラップ、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)可能性があるのと同じプロセス内でプログラムのデバッグは複数の DEs 可能性がありますが含まれるその式が評価されるため、IDE が提供されるインターフェイス同じスレッドで実行されています。  
  
 通常、SDM が委任メカニズムとして機能しますが、ブロードキャスト機構を果たすことがあります。 たとえば、式の評価中に指定されたスレッドでコードを実行できることをすべて DEs を通知するブロードキャスト メカニズムとして、SDM が機能します。 同様に、SDM 停止イベントを受け取るときに実行を停止する必要がありますすべてのプログラムにブロードキャストします。 ステップが呼び出されたときに、SDM にブロードキャストするすべてのプログラム実行を継続できます。 ブレークポイントは、すべて DE にもブロードキャストします。  
  
 現在のプログラム、スレッド、またはスタック フレーム、SDM を追跡しません。 プロセス、プログラム、およびスレッド情報が特定のデバッグ イベントと共に SDM に送信します。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)

