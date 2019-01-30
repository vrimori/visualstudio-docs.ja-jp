---
title: Android のデバッガーのプロパティ (C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 9a4d7baa970008c2de7a3bc28966f7edbad68b21
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036174"
---
# <a name="android-debugger-properties"></a>Android のデバッガーのプロパティ

プロパティ | 説明 | オプション
--- | ---| ---
デバッガーの種類 | デバッグするコードの種類を指定します。 | **ネイティブのみ**<br>**Java のみ**<br>
デバッグ ターゲット | デバッグに使うエミュレーターまたはデバイスを指定します。 エミュレーターが実行されていない場合は、"Android 仮想デバイス (AVD) マネージャー" を使ってデバイスを起動してください。
起動するパッケージ | デバッグする *.apk* の場所を指定します。 アプリケーションをデバッグするときに特定のパッケージ (APK) が開始されるようにこのオプションを選択します。
起動アクティビティ | アプリケーションの起動に使う Android アクティビティは、マニフェストで使われているものと同じでなければなりません。 *AndroidManifest.xml* からリストを取得して動的に設定するには、[適用] を選択します。
追加のシンボル検索パス | デバッグ シンボルの追加の検索パス。
追加の Java ソース検索パス | Java ソース ファイルの追加の検索パス  (デバッガーの種類が [Java のみ] の場合にのみ適用されます)。
