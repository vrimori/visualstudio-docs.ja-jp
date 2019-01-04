---
title: 依存関係図の拡張機能のトラブルシューティング
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d2a47bfd3b5ca927e64645f97f2923300e33d691
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926938"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>依存関係図の拡張機能のトラブルシューティング

このトピックでは、レイヤー モデル拡張機能を作成するときに発生する可能性のある問題について説明します。

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>拡張機能をデバッグして f5 キーを押すと、コマンド、ジェスチャ ハンドラー、検証拡張機能またはカスタム プロパティに表示されない Visual Studio の実験用インスタンスでの依存関係図

1. Visual Studio の実験用インスタンスで拡張機能ソリューションを開きます、**ビルド** メニューのをクリックして**ソリューションのリビルド**します。

2. キーを押して**f5 キーを押して**または**CTRL + F5** Visual Studio の実験用インスタンスを起動します。 依存関係図を開き、拡張機能をテストします。

   必要に応じて、次の手順に進みます。

## <a name="an-old-version-of-my-extension-runs"></a>拡張機能の古いバージョンが実行る

1. Visual Studio の実験用インスタンスが実行されていないことを確認します。

2. 次のフォルダーの削除: %LocalAppData%\Microsoft\VisualStudio\\[バージョン] \ComponentModelCache

   > [!NOTE]
   > %Localappdata% は通常*DriveName*: \Users\\*UserName*\AppData\Local です。

   必要に応じて、次の手順に進みます。

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>古いバージョンの検証結果が表示される、または検証メソッドが呼び出されない

1.  Visual Studio の実験用インスタンスで、**ビルド** メニューのをクリックして**ソリューションのクリーン**。 これにより、前に行った検証分析のキャッシュされている結果がクリアされます。

2.  モデルのレイヤーがコード要素と関連付けられていること、および少なくとも 1 つの依存関係リンクがモデルに存在することを確認します。 検証する項目がない場合、検証は呼び出されません。

3.  検証メソッドは別のプロセスで実行するので、標準のブレークポイントは検証メソッドでは機能しない場合があります。 メソッドをステップ実行する場合は、`System.Diagnostics.Debugger.Launch()` の呼び出しを挿入する必要があります。

4.  **Source.extension.vsixmanifest** 、レイヤー検証プロジェクトの両方を追加したことを確認します、 **MEF コンポーネント**項目と**カスタム拡張機能の種類**] の [**コンテンツ**します。

## <a name="see-also"></a>関連項目

- [依存関係図の拡張](../modeling/extend-layer-diagrams.md)
