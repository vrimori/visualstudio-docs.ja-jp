---
title: "依存関係図の拡張機能のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: "25"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: fae53e45b231292df8b7a6ae8bf4f2babc5d9e88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>依存関係図の拡張機能をトラブルシューティングします。
このトピックでは、レイヤー モデル拡張機能を作成するときに発生する可能性のある問題について説明します。  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>My の拡張機能をデバッグする場合は F5 を押すと、コマンド、ジェスチャ ハンドラー、検証拡張機能、またはカスタム プロパティがない図に表示依存関係の実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  実験用インスタンスで拡張機能ソリューションを開きます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、および、**ビルド** メニューのをクリックして**ソリューションのリビルド**です。  
  
2.  キーを押して**f5 キーを押して**または**ctrl キーを押しながら f5 キーを押して**の実験用インスタンスを起動する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 依存関係ダイアグラムを開くし、拡張機能をテストします。  
  
 必要に応じて、次の手順に進みます。  
  
#### <a name="an-old-version-of-my-extension-runs"></a>拡張機能の古いバージョンが実行る  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンスが実行していないことを確認します。  
  
2.  次のフォルダーを削除: %LocalAppData%\Microsoft\VisualStudio\\[バージョン] \ComponentModelCache  
  
    > [!NOTE]
    >  通常 %localappdata% *DriveName*: \Users\\*UserName*\AppData\Local です。  
  
 必要に応じて、次の手順に進みます。  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>古いバージョンの検証結果が表示される、または検証メソッドが呼び出されない  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の**ビルド** メニューのをクリックして**ソリューションのクリーン**です。 これにより、前に行った検証分析のキャッシュされている結果がクリアされます。  
  
2.  モデルのレイヤーがコード要素と関連付けられていること、および少なくとも 1 つの依存関係リンクがモデルに存在することを確認します。 検証する項目がない場合、検証は呼び出されません。  
  
3.  検証メソッドは別のプロセスで実行するので、標準のブレークポイントは検証メソッドでは機能しない場合があります。 メソッドをステップ実行する場合は、`System.Diagnostics.Debugger.Launch()` の呼び出しを挿入する必要があります。  
  
4.  **Source.extension.vsixmanifest** 、レイヤー検証プロジェクトの両方が追加したことを確認します、 **MEF コンポーネント**項目と**カスタム拡張機能の種類**項目**コンテンツ**です。  
  
## <a name="see-also"></a>関連項目  
 [依存関係図の拡張](../modeling/extend-layer-diagrams.md)
