---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、設定 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 447f32c2e736084a08223b56f4188ca7c8abeea5
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="create-easy-tables"></a>簡易テーブルを作成する

Azure にモバイル アプリを用意し、簡易テーブルを初期化しました。次に、Unity ゲームから送信されたデータを記録するテーブルを作成します。

## <a name="setup-the-crash-heatmap-table"></a>クラッシュ ヒートマップ テーブルを設定する

1. Azure Portal で、[すべてのリソース] をクリックし、前の手順で簡易テーブルに対して構成したモバイル アプリを選択します。

  ![モバイル アプリを選択する](media/vstu_azure-setup-table-schema-image1.png)

2. **[モバイル]** という見出しが表示されるまで下にスクロールし、**[簡易テーブル]** を選択します。 簡易テーブルのためにアプリを初期化することに関する通知はなくなります。  

  ![簡易テーブルを選択する](media/vstu_azure-setup-table-schema-image2.png)

3. **[追加]** ボタンをクリックします。

  ![[追加] をクリックする](media/vstu_azure-setup-table-schema-image3.png)

4. テーブルに "**CrashInfo**" という名前を付け、**[OK]** をクリックします。 残りのオプションは初期設定のままにします。

  > [!WARNING]
  > この名前は、チュートリアルの後半で作成されるデータ モデル クラスの名前と一致する必要があります。

  ![名前を付け、[OK] をクリックする](media/vstu_azure-setup-table-schema-image4.png)

5. 新しいテーブルが作成されると、通知が表示されます。

> [!NOTE]
> 簡易テーブルでは、データが追加されると、テーブル スキーマが動的に作成されます。 つまり、この手順の間、適切なデータ列を手動で設定する必要がありません。

## <a name="setup-the-leaderboard-table"></a>ランキング テーブルを設定する

1. [簡易テーブル] ブレードに戻り、**[追加]** をクリックして 2 つ目のテーブルを追加します。

  ![2 つ目のテーブルを追加する](media/vstu_azure-setup-table-schema-image10.png)

2. 新しいテーブルに "**HighScoreInfo**" という名前を付け、**[OK]** をクリックします。 残りのオプションは初期設定のままにします。

  > [!WARNING]
  > この名前は、チュートリアルの後半で作成されるデータ モデル クラスの名前と一致する必要があります。

  ![名前を付け、[OK] をクリックする](media/vstu_azure-setup-table-schema-image11.png)

3. 新しいテーブルが作成されると、通知が表示されます。


## <a name="next-step"></a>次のステップ

* [開発環境を準備する](visual-studio-tools-for-unity-azure-prepare.md)
