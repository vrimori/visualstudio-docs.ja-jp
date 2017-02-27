---
title: "手順 8: クイズのカスタマイズ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 手順 8: クイズのカスタマイズ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

チュートリアルの最後の部分では、クイズをカスタマイズする方法を説明して、既に学習した内容を掘り下げます。  たとえば、プログラムで解答が決して分数にはならないランダムな除算問題を作成する方法を考えてみます。  さらに詳しく学習するには、`timeLabel` コントロールの色を変更したり、クイズの受け手にヒントを示したりしてみてください。  
  
### クイズをカスタマイズするには  
  
-   クイズの残り時間が 5 秒になったら、**\[BackColor\]** プロパティを設定して、**timeLabel** コントロールの色を赤に変更します \(`timeLabel.BackColor = Color.Red;`\)。  クイズが終了したら元の色に戻します。  
  
-   NumericUpDown コントロールに正しい解答が入力されたら、サウンドを再生してクイズの受け手にヒントを示します  \(クイズの受け手がコントロールの値を変更するたびに実行される、各コントロールの `ValueChanged()` イベントのイベント ハンドラーを記述する必要があります\)。  
  
### 続行または確認するには  
  
-   クイズの完全バージョンをダウンロードするには、「[Complete Math Quiz tutorial sample \(計算クイズのチュートリアルの完全なサンプル\)](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)」を参照してください。  
  
-   次のチュートリアルに進むには、「[チュートリアル 3: 絵合わせゲームの作成](../ide/tutorial-3-create-a-matching-game.md)」を参照してください。  
  
-   チュートリアルの前の手順に戻るには、「[手順 7: 乗算問題と除算問題の追加](../Topic/Step%207:%20Add%20Multiplication%20and%20Division%20Problems.md)」を参照してください。