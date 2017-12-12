---
title: "Visual Studio Tools for Unity と Azure のチュートリアル | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: a7e12508537a3bcda1df7997ba9e390b75b9beaf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>チュートリアル: Unity で Azure 簡易テーブルを使用する

![サンプル ゲームのスクリーンショット](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>はじめに

Azure は、製品利用統計情報やその他のゲーム データをクラウドに保存する、拡張可能なソリューションを提供します。 Unity 2017 がリリースされ、Unity が .NET 4.6 対応になったことで Azure 統合が一層簡単になりました。Azure Mobile Client SDK を利用できます。

以下の手順では、製品利用統計情報やランキング データをクラウドに保存するために Azure を活用する Unity プロジェクトの設定プロセスについて順を追って説明します。

> [!NOTE]
> このプロジェクトでは、Unity 2017 で "Experimental (試験段階)" .NET 4.6 Mono スクリプティング ランタイムが必要になります。 [Unity からは、これがじきに既定となるという声明が出ています](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/)。しかしながら今のところ、"Experimental (試験段階)" というラベルが残っており、問題が発生する可能性があります。

> このチュートリアルでは、Unity PC ビルドから Azure Mobile App バックエンドに接続した例を再現しています。 このドキュメントの執筆時点では、Mac プラットフォームと Android プラットフォームでこのプロジェクトの機能が妨害される問題が判明していました。 問題は解決される予定ですが、日程は決まっていません。 詳細については、Unity の[試験段階スクリプティング フォーラム](https://forum.unity3d.com/forums/experimental-scripting-previews.107/)をご覧ください。

## <a name="download-the-completed-project"></a>完成したプロジェクトをダウンロードする

完成したプロジェクトは GitHub で利用できます。 ただし、このチュートリアルでは、空の新しいプロジェクトから始めるものと想定しています。必要な箇所で、アセットをダウンロードするためのリンクを提供します。

## <a name="walkthrough-steps"></a>チュートリアルの手順

1. [Azure で簡易テーブルを構成する](visual-studio-tools-for-unity-azure-configure.md)
2. [簡易テーブルを作成する](visual-studio-tools-for-unity-azure-setup.md)
3. [開発環境を準備する](visual-studio-tools-for-unity-azure-prepare.md)
4. [データ モデル クラスを作成する](visual-studio-tools-for-unity-azure-data.md)
5. [Azure MobileServiceClient を実装する](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Unity Mono セキュリティ証明書ストアを更新する](visual-studio-tools-for-unity-azure-security.md)
7. [クライアント接続をテストする](visual-studio-tools-for-unity-azure-connection.md)
7. [サンプルのゲーム アセットをインポートする](visual-studio-tools-for-unity-azure-game-assets.md)
8. [サンプルのゲームをテストする](visual-studio-tools-for-unity-azure-game.md)
9. [RaceScene の説明](visual-studio-tools-for-unity-azure-racescene.md)
10. [HeatmapScene の説明](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [LeaderboardScene の説明](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>次のステップ
* [Azure で簡易テーブルを構成する](visual-studio-tools-for-unity-azure-configure.md)
