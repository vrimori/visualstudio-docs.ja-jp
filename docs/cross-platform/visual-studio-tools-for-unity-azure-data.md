---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、データ モデル | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: e3b6064a3947f57ffcbe6422162c6c72fca0ab21
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="create-data-model-classes"></a>データ モデル クラスを作成する

Unity プロジェクトには、Azure Mobile App バックエンドで作成されたテーブルに一致するデータ モデル クラスが含まれている必要があります。

## <a name="create-the-crashinfo-class"></a>CrashInfo クラスを作成する

1. Unity で、ルート **[Assets]** ディレクトリに **Scripts** という名前の新しいフォルダーを追加します。 この新しい [Scripts] フォルダー内でさらに、**Data Models** という名前の新しいフォルダーを作成します。 これはフォルダーを整理する目的で行います。

2. 新しい [Data Models] フォルダー内で、**CrashInfo** という名前の新しい C# スクリプトを作成します。

3. 新しい `CrashInfo` スクリプトを開き、クラス宣言や using ステートメントなど、テンプレート コードがあればそれを削除し、次を追加します。

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > このチュートリアルをうまく進めるには、データ モデル クラスの名前が Azure Mobile App バックエンドで作成された簡易テーブルの名前に一致する必要があります。

## <a name="create-the-highscoreinfo-class"></a>HighScoreInfo クラスを作成する

1. [Data Models] フォルダー内で、**HighScoreInfo** という名前の新しい C# スクリプトを作成します。

2. 新しい `HighScoreInfo` スクリプトを開き、クラス宣言や using ステートメントなど、テンプレート コードがあればそれを削除し、次を追加します。

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>次のステップ

  * [Azure MobileServiceClient を実装する](visual-studio-tools-for-unity-azure-mobile-client.md)
