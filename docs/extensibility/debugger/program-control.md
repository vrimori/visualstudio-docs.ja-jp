---
title: コントロールをプログラム |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c227f38c926cb6d764ddf47541b8bd744eb6f7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102091"
---
# <a name="program-control"></a>プログラムの制御
Visual Studio で、次のステップ実行のすべてのデバッグとルーチンを続行がプログラムのレベルで発生します。  
  
-   特定のフレームの環境で実行される次の命令をコンピューターに設定は、次のステートメントを設定するには、  
  
-   ステップ実行モードを終了する継続を実行するとは、  
  
-   次の命令をステップ実行  
  
-   現在のステップ実行モードを続行  
  
-   プログラムが含まれているスレッドの中断  
  
-   プログラムが含まれているスレッドを再開します。  
  
> [!NOTE]
>  呼び出し履歴の表示は、スレッド レベルで実装されます。 スレッドの呼び出し履歴を表示するときにフレームの情報を列挙するには、すべてのメソッドを実装する必要があります、 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)インターフェイスです。  
  
## <a name="methods-of-program-control"></a>プログラムの制御のメソッド  
 次の表は、メソッドの[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)最小限の機能のデバッグ エンジン (DE) と実行の制御を実装する必要があります。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|停止状態からプログラムに含まれるすべてのスレッドの実行が続行されます。 実行の制御に必要です。|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|停止状態からプログラムに含まれるすべてのスレッドの実行が続行されます。 実行の制御に必要です。|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|特定のスレッドで、手順を実行します。 引き続き、プログラムに含まれるその他のすべてのスレッドを実行します。 実行の制御に必要です。|  
  
 マルチ スレッド プログラムの必要がありますも実装する、 [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)メソッドとのすべてのメソッド、 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md)インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)