---
title: コントロールのプログラム |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b213ee6eca5d132c663e86d6829b688952d150d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537393"
---
# <a name="program-control"></a>プログラムの制御
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プログラムの制御](https://docs.microsoft.com/visualstudio/extensibility/debugger/program-control)します。  
  
Visual Studio でデバッグする場合に、次のステップ実行のすべてとルーチンの続行がプログラムのレベルで発生します。  
  
-   特定のフレームの環境で実行するには、次の命令をコンピューターの設定は、次のステートメントを設定するには、  
  
-   ステップ実行モードを終了するは、継続を実行します。  
  
-   次の命令をステップ実行  
  
-   現在のステップ実行モードを続行  
  
-   プログラムに含まれるスレッドの中断  
  
-   プログラムに含まれるスレッドを再開します。  
  
> [!NOTE]
>  コール スタックの表示は、スレッド レベルで実装されます。 スレッドの呼び出し履歴を表示するときに、フレームの情報を列挙するには、すべてのメソッドを実装する必要があります、 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)インターフェイス。  
  
## <a name="methods-of-program-control"></a>プログラム コントロールのメソッド  
 次の表は、メソッドの[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)最低限機能のデバッグ エンジン (DE) と実行の制御を実装する必要があります。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|停止状態からプログラムに含まれるすべてのスレッドの実行が続行されます。 実行の制御に必要です。|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|停止状態からプログラムに含まれるすべてのスレッドの実行が続行されます。 実行の制御に必要です。|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|特定のスレッドに対して、手順を実行します。 引き続き、プログラムに含まれるその他のすべてのスレッドを実行します。 実行の制御に必要です。|  
  
 マルチ スレッド プログラムは、する必要がありますも実装して、 [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)メソッドとのすべてのメソッド、 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md)インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)

