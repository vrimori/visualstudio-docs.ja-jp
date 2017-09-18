---
title: "手順 8: プレーヤーが勝利したかどうかを確認するメソッドの追加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 手順 8: プレーヤーが勝利したかどうかを確認するメソッドの追加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

楽しいゲームが作成されましたが、完成させるには追加の項目が必要です。  ゲームは、プレーヤーが勝利した時点で終了する必要があるため、プレーヤーが勝利したかどうかを確認する `CheckForWinner()` メソッドを追加する必要があります。  
  
### プレーヤーが勝利したかどうかを確認するメソッドを追加するには  
  
1.  `CheckForWinner()` メソッドを、コードの下部にある `timer1_Tick()` イベント ハンドラーの下に追加します。次のコードのようになります。  
  
     [!code-cs[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]  
  
     このメソッドは、別の `foreach` ループ \(Visual C\# の場合\) または `For Each` ループ \(Visual Basic の場合\) を使用して、TableLayoutPanel 内の各ラベルを処理します。  このメソッドは、等値演算子 \(Visual C\# の場合は `==`、Visual Basic の場合は `=`\) を使用して、各ラベルのアイコンの色をチェックし、それらが背景と一致しているかどうかを確認します。  色が一致する場合は、アイコンが非表示のままになっており、プレーヤーはまだすべてのアイコンを一致させていないことになります。  この場合、プログラムでは `return` ステートメントを使用して、メソッドの残りの処理がスキップされます。  ループが、`return` ステートメントを実行することなくすべてのラベルの処理を終了した場合は、フォーム上のすべてのアイコンが一致していることを意味します。  プログラムでは、MessageBox を表示してプレーヤーの勝利を通知した後に、フォームの `Close()` メソッドを呼び出してゲームを終了します。  
  
2.  次に、ラベルの Click イベント ハンドラーに新しい `CheckForWinner()` メソッドを呼び出させます。  必ず、プログラムでは、プレーヤーがクリックした 2 つ目のアイコンを表示したらすぐに、勝者をチェックするようにしてください。  クリックされた 2 つ目のアイコンの色を設定している行を探して、次のコードに示すように、そのすぐ後で、`CheckForWinner()` メソッドを呼び出します。  
  
     [!code-cs[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]  
  
3.  プログラムを保存し、実行します。  ゲームを実行し、すべてのアイコンを一致させます。  勝利すると、プログラムでは、次の図に示すように MessageBox を表示し、その後にボックスを閉じます。  
  
     ![MessageBox が表示された絵合わせゲーム](../ide/media/express_tut4step8.png "Express\_Tut4Step8")  
MessageBox が表示された絵合わせゲーム  
  
### 続行または確認するには  
  
-   チュートリアルの次の手順に進むには、「[手順 9: その他の機能を試す](../ide/step-9-try-other-features.md)」を参照してください。  
  
-   チュートリアルの前の手順に戻るには、「[手順 7: ペアの表示の維持](../Topic/Step%207:%20Keep%20Pairs%20Visible.md)」を参照してください。