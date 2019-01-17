---
title: 進行状況 ダイアログ ボックスでのデバッグの停止 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3abce02ba1804ff619a7d0f24da35747c2f9ff91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883134"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>[デバッグ操作を停止しています] ダイアログ ボックス
このダイアログ ボックスは、デバッガーがデバッグ セッションを停止しようとしているものの、セッションの停止に時間がかかる場合に表示されます。 デバッグ セッションの停止は通常、非常に速く行われ、このダイアログ ボックスは表示されません。 ただし、デバッグ中のすべてのプロセスからデタッチするのに余分な時間がかかることがあります。 セッションの停止に数分以上かかる場合 (またはデタッチ エラーが発生した場合) は、このダイアログ ボックスが表示されます。 この症状が頻繁に発生する場合は、内部に問題がある可能性があります。製品サポート サービスにお問い合わせください。  
  
 プロセスがデタッチし、このダイアログ ボックスが消えるのを待つか、**[今すぐ停止]** を使って強制的に即時終了します。  
  
 **今すぐ停止**  
 デバッグ セッションを直ちに終了する場合は、このボタンをクリックします。 使用して**今すぐ停止**デバッグ中のプロセスをデタッチするのではなく、終了します。 システム プロセスをデバッグしている場合は、これらのプロセスを **[今すぐ停止]** で終了すると、予想不可能な結果や望ましくない結果になることがあります。  
  
## <a name="see-also"></a>「  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [プログラムのデタッチ](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))