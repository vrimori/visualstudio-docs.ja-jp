---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、ゲーム | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7d0a7da4093b8f90ab76dee55f1ec9ad6dc21679
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-sample-game"></a>サンプルのゲームをテストする

このサンプル ゲームは単純なレーシング ゲームです。プレーヤーの動作に関するデータを記録し、Azure 簡易テーブルに保存します。 このサンプル ゲームには、Azure からデータを読み込み、プレーヤーのためにそれを視覚化するシーンも含まれています。

このセクションでは、サンプル ゲームの遊び方と正しく機能していることを確認する方法について簡単に説明します。 次のセクションでは、サンプル ゲームのしくみについてさらに詳しく説明します。

## <a name="starting-the-game"></a>ゲームを開始する

1. Unity の [Project] ウィンドウで、**[Assets/Azure Easy Tables sample game assets/Scenes]** フォルダーに移動します。

2. **[MenuScene]** をダブルクリックして開きます。

3. Unity の [Game] ウィンドウで、**[aspect ratio dropdown]** をクリックし、**[16:9]** を選択します。

  ![縦横比を設定する](media/vstu_azure-test-sample-game-image1.png)

4. **[Play]** ボタンをクリックし、Unity エディターでゲームを実行します。


## <a name="complete-a-race"></a>レースを完了する

ランキングまたはヒートマップを表示する前に、サンプル データをいくつか作成しておくことをお勧めします。少なくとも 1 回はレースを完了させましょう。

1. Unity エディターでゲームを起動している状態で **[Race!]** ボタンをクリックし、 新しいレースを開始します。

2. **WASD** または**方向キー**を使用して車両を操作し、時計回りにコースを完走します。サンプルを取るために、壁に何回かクラッシュしてみてください。 Unity コンソールのデバッグ出力は、衝突が記録された瞬間を示します。

  >[!NOTE]
  > 車両が横転し、続行できない場合、**[Restart]** をクリックしてください。 データはラップの完了時にのみ Azure に送信されます。

  ![レースを開始する](media/vstu_azure-test-sample-game-image2.png)

3. チェッカーフラッグを通過すると、**[Finished]** メッセージが表示されます。 この時点で、クラッシュ データが Azure にアップロードされます。

4. ラップタイムが 10 位内に入った場合、スコアボードに名前を入力するように求められます。 名前を入力し、**[Submit]** をクリックします。

  ![レースを開始する](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>ヒートマップを表示する

1. レース シーンで **[View Crash Heatmap]** ボタンをクリックするか、メイン メニューで **[Crash Heatmap]** を選択します。

2. ヒートマップ シーンは Azure の CrashInfo テーブルからデータを読み込み、プレーヤーがコースの壁にクラッシュした場所に赤い透明な球体を表示します。重複する領域で複数のクラッシュが発生した場合、球体は一層明るく表示されます。

  ![ヒートマップ](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>ランキングを表示する

1. レース シーンまたはメイン メニューで **[Leaderboard]** ボタンをクリックします。

2. ランキング シーンは Azure の HighScoreInfo テーブルからハイスコア データを読み込み、ハイスコア エントリごとにプレーヤーの名前とラップタイムを表示します。

  ![ランキング](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>次のステップ

* [RaceScene の説明](visual-studio-tools-for-unity-azure-racescene.md)
