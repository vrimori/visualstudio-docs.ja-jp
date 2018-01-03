---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、ゲーム アセット | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 19b98dc472b9e01529725b95133d289edff6334d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="import-sample-game-assets"></a>サンプルのゲーム アセットをインポートする

テストの結果、中心的機能が動作することが証明されたので、次にサンプルのゲーム アセットをインポートします。

## <a name="import-package"></a>パッケージをインポートする

1. [サンプルのゲーム アセット パッケージ](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage)をダウンロードします。

2. Unity プロジェクトを開いていることを確認し、ダウンロード場所に移動し、ファイルをダブルクリックします。 Unity にインポート ダイアログが表示されます。

3. **[All]** をクリックし、**[Import]** をクリックします。 ダウンロードの進捗状況バーが表示されます。ダウンロードが完了するまで待ちます。

  ![パッケージをインポートする](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>ビルド設定にシーンを追加する

ファイルのインポートが完了したら、必要なシーン ファイルを Unity プロジェクトのビルド設定に追加する必要があります。

1. Unity の [Project] ウィンドウで、**[Azure Easy Tables sample game assets/Scenes]** ディレクトリに移動します。

2. Unity メニューから、**[File]、[Build Settings...]** の順に選択します。[Build Settings] ダイアログが表示されます。

3. [Project] ウィンドウの **HeatmapScene** ファイル、**LeaderboardScene** ファイル、**MenuScene** ファイル、**RaceScene** ファイルを [Build Settings] ダイアログの **[Scenes In Build]** セクションにドラッグします。

  ![パッケージをインポートする](media/vstu_azure-import-sample-assets-image2.png)

4. Unity メニューから、**[File]、[Save Project]** の順に選択し、ビルド設定が保存されたことを確認します。

## <a name="next-step"></a>次のステップ

* [サンプルのゲームをテストする](visual-studio-tools-for-unity-azure-game.md)