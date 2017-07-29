---
title: "手順 9: その他の機能を試す | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: b0ef009dae267ca566a41bad3d6f0a9ef81cb02b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---
# <a name="step-9-try-other-features"></a>手順 9: その他の機能を試す
さらに詳しく学習するために、アイコンおよび色の変更、ゲーム タイマーの追加、サウンドの追加を試します。 ゲームをよりやりがいのあるものにするために、ボードの拡大およびタイマーの調整を試します。  
  
 サンプルの完全バージョンをダウンロードするには、「[Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba)」 (絵合わせゲームのチュートリアルの完全なサンプル)を参照してください。  
  
### <a name="to-try-other-features"></a>その他の機能を試すには  
  
-   アイコンおよび色を、選択したものに置き換えます。  
  
    > [!TIP]
    >  ラベルの [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) プロパティを見てみてください。  
  
-   プレーヤーが勝利するまでにかかる時間の長さを追跡するゲーム タイマーを追加します。  
  
    > [!TIP]
    >  そのためには、フォーム上の TableLayoutPanel の上に経過時間を表示するためのラベルを追加し、その時間を追跡するための別のタイマーを追加します。 プレーヤーがゲームを開始するとタイマーを開始し、最後の 2 つのアイコンが一致した後にタイマーを停止するコードを使用します。  
  
-   プレーヤーが一致を見つけたときのサウンド、プレーヤーが一致しない 2 つのアイコンを表示したときの別のサウンド、およびプログラムでアイコンが再度非表示になるときの 3 つ目のサウンドを追加します。  
  
    > [!TIP]
    >  サウンドを再生するには、System.Media 名前空間を使用できます。 詳細については、「[Windows フォーム アプリでサウンドを再生する (C# .NET)](http://youtu.be/qOh4ooHg1UU)」または「[Visual Basic でオーディオを再生する](http://youtu.be/-4oPDeQrtMs)」を参照してください。  
  
-   ボードを拡大して、ゲームをより難しくします   
  
    > [!TIP]
    >  TableLayoutPanel に行や列を追加する以上のことを行う必要があります。作成するアイコンの数を検討する必要もあります。  
  
-   プレーヤーが、選択が遅すぎて一定時間内に 2 つ目のアイコンをクリックしなかった場合に、1 つ目のアイコンを非表示にするようにして、ゲームをよりやりがいのあるものにします。  
  
### <a name="to-continue-or-review"></a>続行または確認するには  
  
-   プログラミングに行き詰まった場合や疑問がある場合は、MSDN フォーラムのいずれかに質問を投稿してみてください。 [Visual Basic フォーラム](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral)、および [Visual C# フォーラム](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral)を参照してください。  
  
-   無料で利用できる便利なビデオ学習リソースがあります。 Visual Basic でのプログラミングの詳細については、「[Visual Basic の基礎: 入門者向けの開発](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)」を参照してください。 Visual C# でのプログラミングの詳細については、「[C# の基礎: 入門者向けの開発](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)」を参照してください。  
  
-   チュートリアルの前の手順に戻るには、「[手順 8: プレーヤーが勝利したかどうかを確認するメソッドの追加](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)」を参照してください。
