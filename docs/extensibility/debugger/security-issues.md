---
title: "セキュリティの問題 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>セキュリティ上の問題
Visual Studio を使用してプログラムをデバッグするには、必要なアクセス許可は、開発者がプログラムを実行する必要があるものと同じです。 これには、ほとんどの場合 (インターネット インフォメーション サービスなど、他のサービスに関連する状況によってはより高いレベルのアクセス許可にあります) のリモート デバッグが含まれます。  
  
 Visual Studio の実行中に、プロセスのデバッグ マネージャー (PDM) は、ローカル コンピューター上のデバッグ プロセスを追跡します。 リモートでリモート デバッグを処理し、PDM を利用する開発者によって msvsmon.exe と呼ばれるプログラムを起動します。 なお、msvsmon.exe がサービスではないと、そのコンピューターにリモート デバッグを有効にするのには手動で開始する必要があります。Visual Studio (msvsmon.exe) が実行されていない場合は、デバッグ用のプロセスが追跡されません。  
  
 これは、開発者がない特殊なアクセス許可を持つかどうかが起動されたプログラムをデバッグすることを意味します。 であっても、開発者は、その他の人が同じセキュリティ グループのメンバーである場合は、他のユーザーによって開始されたプロセスをデバッグできます。 リモート デバッグを有効にする必要があるだけでをコピーするために必要なファイルをリモート コンピューターのして msvsmon.exe を開始し、(を参照してください[リモート デバッグ](../../debugger/remote-debugging.md)詳細)。  
  
## <a name="see-also"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [プロセスのデバッグ マネージャー](../../extensibility/debugger/process-debug-manager.md)   
 [Remote Debugging](../../debugger/remote-debugging.md)
