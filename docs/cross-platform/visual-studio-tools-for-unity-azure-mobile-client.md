---
title: "Visual Studio Tools for Unity と Azure のチュートリアル、モバイル クライアント | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 294942641aa0739d105a888f4fbfe6ba9cf05a16
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>Azure MobileServiceClient を実装する

Azure Mobile Client SDK の中心となるのが <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a> です。これにより、モバイル アプリのバックエンドにアクセスできます。

## <a name="locate-the-url-of-the-mobile-app-backend"></a>モバイル アプリ バックエンドの URL を見つける

`MobileServiceClient` コンストラクターはパラメーターとしてモバイル アプリ URL を受け取ります。そこで、先に進む前にこの URL を見つけます。

1. Azure Portal で、**[App Services]** ボタンをクリックします。

    ![App Services をクリックする](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. モバイル アプリのエントリをクリックします。

    ![モバイル アプリをクリックする](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. モバイル アプリ バックエンドの URL をコピーします。

    ![URL をコピーする](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>シングルトンの MobileServiceClient を作成する

`MobileServiceClient` のインスタンスは 1 つだけにします。そこで、このチュートリアルでは、シングルトン パターンのバリエーションを利用します。

1. Unity プロジェクトの **[Assets/Scripts]** ディレクトリ内で、**AzureMobileServiceClient** という名前の新しい C# スクリプトを作成します。

2. `AzureMobileServiceClient` スクリプトを開き、using ステートメントやクラス宣言など、既存のテンプレート コードがあればそれを削除します。

3. 次のコードを追加します。

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > IntelliSense で Microsoft.WindowsAzure 名前空間が認識されない場合、「[開発環境を準備する]()」セクションのすべての手順を完了していることを確認してください。

4. 先のコードで、`MOBILE_APP_URL` をモバイル アプリ バックエンドの URL に変更します。

## <a name="next-step"></a>次のステップ

* [Unity Mono セキュリティ ストアを更新する](visual-studio-tools-for-unity-azure-security.md)
