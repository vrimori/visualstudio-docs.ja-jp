---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、接続 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: cb2ce447f21231b98d6464824ba7d088fee16cce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-client-connection"></a>クライアント接続をテストする

シングルトンの AzureMobileServiceClient が作成されたので、次にクライアント接続をテストします。

## <a name="create-the-testclientconnection-script"></a>TestClientConnection スクリプトを作成する

1. Unity の **[Scripts]** フォルダー内で、**TestClientConnection** という名前の新しい C# スクリプトを作成します。

2. Visual Studio でスクリプトを開き、テンプレート コードがあればそれを削除し、次を追加します。

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. Unity の **[GameObject]** メニューで、**[GameObject]、[Create Empty]** の順に選択し、Unity シーンで空の GameObject を作成します。 名前を **TestClientConnection** に変更します。

4. Unity の **[Project]** ウィンドウの TestClientConnection スクリプトを **[Hierarchy]** ウィンドウの TestClientConnection GameObject に**ドラッグ**します。

5. Unity メニューで、**[File]、[Save Scene as...]** の順に選択します。シーンに **Client Connection Test** という名前を付け、**[Save]** をクリックします。

5. Unity の **[Play]** ボタンをクリックし、[Console] ウィンドウを観察します。 アサーションに失敗がないことを確認します。

6. Azure Portal で CrashInfo 簡易テーブルを開きます。 **X,Y,Z** 座標が **(1, 2, 3)** で、**deleted** 列の値が **true** のエントリが表示されるはずです。 テストを実行するたびに、値が同じでも ID が一意の新しいエントリがテーブルに追加されます。

  ![簡易テーブルのエントリ](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>次のステップ
* [サンプルのゲーム アセットをインポートする](visual-studio-tools-for-unity-azure-game-assets.md)
