---
title: 進行状況 ダイアログ ボックスでのデバッグの停止 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.stopnow
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 440d71a5a84ba5cd9390cc0ba9dfb6319be61cd2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190477"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>[デバッグ操作を停止しています] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このダイアログ ボックスは、デバッガーがデバッグ セッションを停止しようとしているものの、セッションの停止に時間がかかる場合に表示されます。 デバッグ セッションの停止は通常、非常に速く行われ、このダイアログ ボックスは表示されません。 ただし、デバッグ中のすべてのプロセスからデタッチするのに余分な時間がかかることがあります。 セッションの停止に数分以上かかる場合 (またはデタッチ エラーが発生した場合) は、このダイアログ ボックスが表示されます。 この症状が頻繁に発生する場合は、内部に問題がある可能性があります。製品サポート サービスにお問い合わせください。  
  
 デタッチするプロセスとの非表示には、このダイアログ ボックスまで待つか、使用することができます、**今すぐ停止**強制的に即時終了ボタンをクリックします。  
  
 **停止するようになりました**  
 デバッグ セッションを直ちに終了する場合は、このボタンをクリックします。 使用して**今すぐ停止**デバッグ中のプロセスをデタッチするのではなく、終了します。 システム プロセスをデバッグする場合は、これらのプロセスを終了して**今すぐ停止**が予期しないと、望ましくない効果。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [プログラムのデタッチ](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)



