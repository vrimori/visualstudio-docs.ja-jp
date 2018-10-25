---
title: '手順 8: プレーヤーが勝利したかどうかを確認するメソッドの追加 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 278d8d71378c0d14047fe8e012fed21951101548
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306634"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>手順 8: プレーヤーが勝利したかどうかを確認するメソッドの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

楽しいゲームが作成されましたが、完成させるには追加の項目が必要です。 ゲームは、プレーヤーが勝利した時点で終了する必要があるため、プレーヤーが勝利したかどうかを確認する `CheckForWinner()` メソッドを追加する必要があります。  
  
### <a name="to-add-a-method-to-verify-whether-the-player-won"></a>プレーヤーが勝利したかどうかを確認するメソッドを追加するには  
  
1.  `CheckForWinner()` メソッドを、コードの下部にある `timer1_Tick()` イベント ハンドラーの下に追加します。次のコードのようになります。  
  
     [!code-csharp[VbExpressTutorial4Step8#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial4Step8#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#10)]  
  
     このメソッドは、別の `foreach` ループ (Visual C# の場合) または `For Each` ループ (Visual Basic の場合) を使用して、TableLayoutPanel 内の各ラベルを処理します。 このメソッドは、等値演算子 (Visual C# の場合は `==`、Visual Basic の場合は `=`) を使用して、各ラベルのアイコンの色をチェックし、それらが背景と一致しているかどうかを確認します。 色が一致する場合は、アイコンが非表示のままになっており、プレーヤーはまだすべてのアイコンを一致させていないことになります。 この場合、プログラムでは `return` ステートメントを使用して、メソッドの残りの処理がスキップされます。 ループが、`return` ステートメントを実行することなくすべてのラベルの処理を終了した場合は、フォーム上のすべてのアイコンが一致していることを意味します。 プログラムでは、MessageBox を表示してプレーヤーの勝利を通知した後に、フォームの `Close()` メソッドを呼び出してゲームを終了します。  
  
2.  次に、ラベルの Click イベント ハンドラーに新しい `CheckForWinner()` メソッドを呼び出させます。 必ず、プログラムでは、プレーヤーがクリックした 2 つ目のアイコンを表示したらすぐに、勝者をチェックするようにしてください。 クリックされた 2 つ目のアイコンの色を設定している行を探して、次のコードに示すように、そのすぐ後で、`CheckForWinner()` メソッドを呼び出します。  
  
     [!code-csharp[VbExpressTutorial4Step8#11](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs#11)]
     [!code-vb[VbExpressTutorial4Step8#11](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb#11)]  
  
3.  プログラムを保存し、実行します。 ゲームを実行し、すべてのアイコンを一致させます。 勝利すると、プログラムでは、次の図に示すように MessageBox を表示し、その後にボックスを閉じます。  
  
     ![MessageBox が表示された絵合わせゲーム](../ide/media/express-tut4step8.png "Express_Tut4Step8")  
MessageBox が表示された絵合わせゲーム  
  
### <a name="to-continue-or-review"></a>続行または確認するには  
  
-   次のチュートリアルの手順に進む場合は、「[手順 9: その他の機能を試す](../ide/step-9-try-other-features.md)」を参照してください。  
  
-   前のチュートリアルの手順に戻る場合は、「[手順 7: ペアの表示の維持](../ide/step-7-keep-pairs-visible.md)」を参照してください。



