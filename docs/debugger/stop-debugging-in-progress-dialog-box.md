---
title: "進行状況 ダイアログ ボックスでデバッグを停止 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords: Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c056882d1a5c7eca4a7e09d040753d139c89b5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="stop-debugging-in-progress-dialog-box"></a>[デバッグ操作を停止しています] ダイアログ ボックス
このダイアログ ボックスは、デバッガーがデバッグ セッションを停止しようとしているものの、セッションの停止に時間がかかる場合に表示されます。 デバッグ セッションの停止は通常、非常に速く行われ、このダイアログ ボックスは表示されません。 ただし、デバッグ中のすべてのプロセスからデタッチするのに余分な時間がかかることがあります。 セッションの停止に数分以上かかる場合 (またはデタッチ エラーが発生した場合) は、このダイアログ ボックスが表示されます。 この症状が頻繁に発生する場合は、内部に問題がある可能性があります。製品サポート サービスにお問い合わせください。  
  
 プロセスがデタッチし、このダイアログ ボックスが表示されなくなった、待つかを使用して、**今すぐ停止**強制的に即時終了ボタンをクリックします。  
  
 **今すぐ停止します。**  
 デバッグ セッションを直ちに終了する場合は、このボタンをクリックします。 使用して**今すぐ停止**デバッグ中のプロセスをデタッチするのではなく、終了されます。 システム プロセスをデバッグする場合は、これらのプロセスを終了して**今すぐ停止**が予期しないと、望ましくない影響します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [プログラムのデタッチ](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)