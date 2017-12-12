---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、RaceScene | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 304fb69ab6e5da058cd3d2a4d6de202fa042b8f9
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="racescene-explanation"></a>RaceScene の説明

RaceScene では Unity の [Standard Assets](https://www.assetstore.unity3d.com/en/#!/content/32351) を利用し、基本的なレーシング ゲームプレイとレベルを作成します。 このセクションでは、関連する GameObjects とそのスクリプトを RaceScene 階層の一覧表示順序で説明します。下のスクリーンショットの順序になります。

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

**MultipurposeCameraRig** は Standard Assets パッケージの **Cameras** に含まれています。 その [Inspector] プロパティは、適切なスピードで車両を追いかけるように調整されています。

## <a name="levelgeometry"></a>LevelGeometry

LevelGeometry プレハブは、整理目的で使用される空の GameObject です。 その子の GameObjects は、プレイ可能空間を構成します。 床、壁、傾斜、障害物はすべて、Standard Assets の **Prototyping** パッケージのプレハブから作られます。

**大切な注意点が 1 つあります。**Azure で記録するクラッシュで物体をテストするには、**Wall** タグを適用しておく必要があります。

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Car

**Car** プレハブは、Standard Assets パッケージの **Vehicles** に含まれています。 唯一の変更点は、**RecordCrashInfo** スクリプト コンポーネントが追加されることです。

### <a name="recordcrashinfo"></a>RecordCrashInfo

このスクリプトは `OnCollisionEnter` のクラッシュを確認し、一覧に記録します。 `crashRecordingCooldown` と `crashRecordingMinVelocity` によって、関連があるデータ セットを記録するために、ゲーム内でクラッシュと見なされるものが限定されます。

`RaceFinished` イベントが発生すると、`UploadNewCrashDataAsync` は一覧の各クラッシュを Azure の CrashInfo 簡易テーブルに送信します。

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>checkpoints

このレベルには、4 つの GameObject と **Checkpoint** スクリプト コンポーネントがあります。 このチェックポイントにより、コースを外れて走行した場合、プレーヤーはレースを完走できません。チェックポイントは完走時のタイムも検出します。 完走した時点で `RaceFinished` イベントが呼び出されます。

## <a name="invisible-collision"></a>見えない衝突

プレーヤーをコース内にとどめるための「Invisible Collision (見えない衝突)」として、MeshRenderer コンポーネントを無効にした標準の原始的立方体 (Primitive Cube) が使用されます。 また、車が宙に浮かんだとき、見えない壁にぶつかってうまく跳ねるように、あるいは、プレーヤーが見えない壁にぶつかったり、見えない壁を滑り落ちたり、見える壁の上に着地したりしないように、**Bouncy** という物理マテリアルが適用されます。

## <a name="recordhighscore"></a>RecordHighScore

このスクリプトは、プレーヤーが新しいハイスコアを記録したかどうかを確認します。 記録した場合、`enterNamePopup` が表示されます。このポップアップでは、プレーヤーは自分の名前を入力し、**[Submit]** をクリックできます。

プレーヤーの名前が送信されると、`UploadNewHighScoreAsync` が呼び出され、新しいハイスコアが Azure の HighScoreInfo 簡易テーブルに送信されます。

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>次のステップ

* [HeatmapScene の説明](visual-studio-tools-for-unity-azure-heatmapscene.md)
