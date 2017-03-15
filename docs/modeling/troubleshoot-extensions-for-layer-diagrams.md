---
title: "依存関係図に関する拡張機能のトラブルシューティングを行う |Microsoft ドキュメント"
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
caps.latest.revision: 25
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 26a1992fb9c49c670740a8d4a9a992df3d0a86db
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>依存関係図に関する拡張機能のトラブルシューティングを行う
このトピックでは、レイヤー モデル拡張機能を作成するときに発生する可能性のある問題について説明します。  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>My の拡張機能をデバッグする f5 キーを押すと、コマンド、ジェスチャ ハンドラー、検証拡張機能またはカスタム プロパティに表示されませんの実験用インスタンスで、依存関係図[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  実験用インスタンスで拡張機能ソリューションを開きます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、および、**ビルド** メニューのをクリックして**ソリューションのリビルド**します。  
  
2.  キーを押して**f5 キーを押して**または**CTRL + F5**の実験用インスタンスを起動する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 依存関係図を開き、拡張機能をテストします。  
  
 必要に応じて、次の手順に進みます。  
  
#### <a name="an-old-version-of-my-extension-runs"></a>拡張機能の古いバージョンが実行る  
  
1.  
          [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンスが実行していないことを確認します。  
  
2.  次のフォルダーを削除します %LocalAppData%\Microsoft\VisualStudio\\[バージョン] \ComponentModelCache。  
  
    > [!NOTE]
    >  %Localappdata% は通常、 *DriveName*: \Users\\*UserName*\AppData\Local です。  
  
 必要に応じて、次の手順に進みます。  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>古いバージョンの検証結果が表示される、または検証メソッドが呼び出されない  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の**ビルド** メニューのをクリックして**ソリューションのクリーン**します。 これにより、前に行った検証分析のキャッシュされている結果がクリアされます。  
  
2.  モデルのレイヤーがコード要素と関連付けられていること、および少なくとも&1; つの依存関係リンクがモデルに存在することを確認します。 検証する項目がない場合、検証は呼び出されません。  
  
3.  検証メソッドは別のプロセスで実行するので、標準のブレークポイントは検証メソッドでは機能しない場合があります。 メソッドをステップ実行する場合は、`System.Diagnostics.Debugger.Launch()` の呼び出しを挿入する必要があります。  
  
4.  **Source.extension.vsixmanifest** 、レイヤー検証プロジェクトで両方を追加したことを確認、 **MEF コンポーネント**項目と**カスタム拡張機能の種類**項目の下にある**コンテンツ**します。  
  
## <a name="see-also"></a>関連項目  
 [依存関係図を拡張します。](../modeling/extend-layer-diagrams.md)

