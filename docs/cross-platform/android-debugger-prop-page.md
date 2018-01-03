---
title: "Android のデバッガーのプロパティ (C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
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
ms.workload: xplat-cplusplus
ms.openlocfilehash: d8caf579aa73a77f3c20162ae775411df551f373
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
