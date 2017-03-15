---
title: "依存関係図を拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 39
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ad673b1bc7d3089c37717dd7e1f1fce4e86d8100
ms.lasthandoff: 02/22/2017

---
# <a name="extend-dependency-diagrams"></a>依存関係図を拡張します。
作成し、依存関係図を更新し、Visual Studio での依存関係図と照らし合わせてプログラム コードの構造を検証するコードを記述することができます。 図のショートカット (コンテキスト) メニューに表示するコマンドを追加し、ドラッグ アンド ドロップ ジェスチャをカスタマイズし、テキスト テンプレートからレイヤー モデルにアクセスすることができます。 これらの拡張機能を VSIX (Visual Studio Integration Extension) にパッケージ化し、他の Visual Studio ユーザーに配布することができます。  
  
 詳細については、依存関係図を参照してください。  
  
-   [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)  
  
-   [依存関係図: ガイドライン](../modeling/layer-diagrams-guidelines.md)  
  
-   [コードから依存関係図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [依存関係図をコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="a-nameprereqsa-requirements"></a><a name="prereqs"></a> 要件  
 レイヤー拡張機能を開発するコンピューターに以下の項目がインストールされている必要があります。  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   Modeling SDK for Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 適切なバージョンの Visual Studio をレイヤー拡張機能を実行するコンピューターにインストールしておく必要があります。 詳細については、次を参照してください。[レイヤー モデル拡張機能を配置](../modeling/deploy-a-layer-model-extension.md)します。  
  
 依存関係図をサポートする Visual Studio のバージョンを参照してください[アーキテクチャとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [依存関係図にコマンドおよびジェスチャを追加します。](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [依存関係ダイアグラムへのカスタム アーキテクチャ検証を追加します。](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [カスタム プロパティの依存関係図を追加します。](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [プログラム コードでレイヤー モデル内を移動し、レイヤー モデルを更新する](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [レイヤー モデル拡張機能の配置](../modeling/deploy-a-layer-model-extension.md)  
  
 [依存関係図に関する拡張機能のトラブルシューティングを行う](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>関連項目  
 [定義およびモデリング拡張機能をインストールします。](../modeling/define-and-install-a-modeling-extension.md)   
 [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)   
 [依存関係図: ガイドライン](../modeling/layer-diagrams-guidelines.md)   
 [コードから依存関係図を作成します。](../modeling/create-layer-diagrams-from-your-code.md)   
 [依存関係図をコードを検証します。](../modeling/validate-code-with-layer-diagrams.md)   

