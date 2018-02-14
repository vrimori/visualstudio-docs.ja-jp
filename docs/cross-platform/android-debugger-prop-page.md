---
title: "Android のデバッガーのプロパティ (C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 3ca25e560a4bc3060d86972b4000b3d9ad59ba1f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="android-debugger-properties"></a>Android のデバッガーのプロパティ

プロパティ | 説明 | オプション
--- | ---| ---
デバッガーの種類 | デバッグするコードの種類を指定します。 | **ネイティブのみ**<br>**Java のみ**<br>
デバッグ ターゲット | デバッグに使うエミュレーターまたはデバイスを指定します。 エミュレーターが実行されていない場合は、"Android 仮想デバイス (AVD) マネージャー" を使ってデバイスを起動してください。
起動するパッケージ | デバッグする .apk の場所を指定します。 アプリケーションをデバッグするときに特定のパッケージ (APK) が開始されるようにこのオプションを選択します。
起動アクティビティ | アプリケーションの起動に使う Android アクティビティは、マニフェストで使われているものと同じでなければなりません。 AndroidManifest.xml からリストを取得して動的に設定するには、[適用] を押してください。
追加のシンボル検索パス | デバッグ シンボルの追加の検索パス。
追加の Java ソース検索パス | Java ソース ファイルの追加の検索パス  (デバッガーの種類が [Java のみ] の場合にのみ適用されます)。
