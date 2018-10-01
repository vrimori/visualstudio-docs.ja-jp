---
title: Visual Basic でのステートメントの停止 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fcb4e3018dad53ef869748a4394363dba78f71c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533524"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic の Stop ステートメント
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual basic の Stop ステートメント](https://docs.microsoft.com/visualstudio/debugger/stop-statements-in-visual-basic)します。  
  
ブレークポイントを設定する別の方法として、Visual Basic の Stop ステートメントをプログラムで使用できます。 デバッガーが Stop ステートメントを実行すると、プログラムの実行が中断されます。つまり、中断モードに入ります。 C# では、System.Diagnostics.Debugger.Break への呼び出しを使用して、プログラムの実行を中断できます。  
  
 ソース コードを編集することで Stop ステートメントを設定または削除できます。 デバッガー コマンドでは、ブレークポイントを設定またはクリアできますが、Stop ステートメントを設定またはクリアすることはできません。  
  
 Stop ステートメントは、End ステートメントとは異なり、変数をリセットしたり、デザイン モードに戻ったりすることはありません。 アプリケーションの実行を継続するには [デバッグ] メニューの [続行] をクリックします。  
  
 Just-In-Time デバッグが有効な場合は、デバッガーの外部で実行中の Visual Basic アプリケーションの Stop ステートメントによって、デバッガーが起動します。 Just-In-Time デバッグが有効でない場合、Stop ステートメントは End ステートメントと同様に機能し、実行を終了します。 QueryUnload イベントや Unload イベントが発生しないため、Visual Basic アプリケーションのリリース バージョンに設定されたすべての Stop ステートメントを削除する必要があります。 詳細については、次を参照してください。 [Just-In-Time デバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)します。  
  
 Stop ステートメントを削除しなくて済むようにするには、次のような条件付きコンパイルを使用できます。  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Stop ステートメントの代わりに、Assert ステートメントを使用する方法もあります。 Debug.Assert ステートメントは、指定した条件を満たさない場合にだけ実行を中断し、リリース バージョンのビルド時に自動的に削除されます。 詳細については、次を参照してください。[マネージ コードでアサーション](../debugger/assertions-in-managed-code.md)します。 デバッグ バージョンで常に実行を中断する Assert ステートメントが必要な場合は、次のコードを使用します。  
  
```  
Debug.Assert(false)  
```  
  
 また、Debug.Fail メソッドを使用する方法もあります。  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [C#、F#、および Visual Basic のプロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)



