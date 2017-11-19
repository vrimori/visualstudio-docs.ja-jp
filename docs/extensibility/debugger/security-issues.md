---
title: "セキュリティの問題 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8061c419f81493e56a58df8fefbe4d3362d43e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="security-issues"></a>セキュリティ上の問題
Visual Studio を使用してプログラムをデバッグするには必要なアクセス許可は、開発者がプログラムを実行する必要があるものと同じです。 これは、ほとんどの状況が (インターネット インフォメーション サービスなど、他のサービスに関連するいくつかの状況はより高いレベルのアクセス許可にあります) のリモート デバッグが含まれます。  
  
 Visual Studio の実行中に、プロセスのデバッグ マネージャー (PDM) は、ローカル コンピューターでデバッグ プロセスを追跡します。 リモートで msvsmon.exe と呼ばれるプログラムは、リモート デバッグを処理し、PDM を利用できるようにする開発者によってが開始されます。 (その msvsmon.exe がサービスではないと、そのコンピューター上でリモート デバッギングを有効にするのには手動で開始する必要がありますに注意してください)。Visual Studio (msvsmon.exe) が実行されていない場合、デバッグ用のプロセスは追跡されません。  
  
 これは、開発者が特別な権限を自分が起動されたプログラムをデバッグすることを意味します。 であっても、開発者は、その他の人が、同じセキュリティ グループのメンバーである場合は、他のユーザーによって開始されたプロセスをデバッグできます。 リモート デバッグを有効にする必要があるだけで、必要なをコピーするファイルをリモート コンピューターし、msvsmon.exe を起動し、(を参照してください[リモート デバッグ](../../debugger/remote-debugging.md)詳細)。  
  
## <a name="see-also"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [プロセスのデバッグ マネージャー](../../extensibility/debugger/process-debug-manager.md)   
 [Remote Debugging](../../debugger/remote-debugging.md)