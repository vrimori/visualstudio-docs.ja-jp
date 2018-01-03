---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、HeatmapScene | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 472b6d5adae5e23007b9c1aa4d9c75118a94e1cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="heatmapscene-explanation"></a>HeatmapScene の説明

HeatmapScene には、**LevelGeometry** プレハブのインスタンスが含まれています。 この方法で、Azure から読み込まれたクラッシュ座標が同位のアートに正しくマッピングされます。

## <a name="heatmap-script"></a>Heatmap スクリプト

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync` は Azure の CrashInfo 簡易テーブルに接続し、<a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx">`ToListAsync`</a> を利用してそのすべてのエントリを一覧に追加します。

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList` は Azure から受け取ったクラッシュ一覧を反復処理し、エントリごとにクラッシュ マーカーをインスタンス化します。

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

ユーザーが **[Clear Data]** ボタンを押すと、`DeleteCrashDataAsync` が呼び出されます。 これはクラッシュのローカル一覧を反復処理し、エントリごとに <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx">`DeleteAsync`</a> を呼び出します。 これで簡易テーブルの各エントリの **[Deleted]** 列が **true** に設定されます。 `ToListAsync` は、削除されたこれらのエントリを無視します。

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>次のステップ

* [LeaderboardScene の説明](visual-studio-tools-for-unity-azure-leaderboardscene.md)